## 2026/10/27時点でのPythonのプログラム

```python
import pyaudio
import numpy as np
import matplotlib.pyplot as plt

# --- 設定 ---
CHUNK = 4096            # 1度に読み込むデータ量（周波数分解能に影響）
RATE = 96000
# サンプリングレート（標準的な48kHz）
FORMAT = pyaudio.paInt16 # 16bitフォーマット
CHANNELS = 1            # モノラル

# PyAudioの初期化
p = pyaudio.PyAudio()
stream = p.open(format=FORMAT,
                channels=CHANNELS,
                rate=RATE,
                input=True,
                frames_per_buffer=CHUNK)

# Matplotlibのグラフ設定
plt.ion() # インタラクティブモードON（リアルタイム描画用）
# 2行1列でグラフを作成し、サイズを少し縦長に調整
fig, (ax_wave, ax_fft) = plt.subplots(2, 1, figsize=(10, 8))

# --- 1. 時間領域（波形）グラフの設定 ---
# X軸を時間（ミリ秒）に換算
x_time = np.arange(0, CHUNK) / RATE * 1000 
line_wave, = ax_wave.plot(x_time, np.zeros(CHUNK))
ax_wave.set_title("Real-time Audio Waveform")
ax_wave.set_xlabel("Time (ms)")
ax_wave.set_ylabel("Amplitude (16bit)")
ax_wave.set_xlim(0, CHUNK / RATE * 1000)
ax_wave.set_ylim(- 5000,  5000) # int16の最大・最小値
ax_wave.grid(True)

# --- 2. 周波数領域（FFT）グラフの設定 ---
x_freq = np.fft.rfftfreq(CHUNK, 1.0 / RATE) # X軸（周波数）の計算
line_fft, = ax_fft.plot(x_freq, np.zeros(len(x_freq)))
ax_fft.set_title("EFNMR Real-time FFT Analyzer")
ax_fft.set_xlabel("Frequency (Hz)")
ax_fft.set_ylabel("Amplitude")
ax_fft.set_xlim(0, 5000) # 観測したい帯域（0Hz 〜 5kHz）に絞る
ax_fft.set_ylim(0,  50)  # Y軸の最大値（信号の大きさによって調整してください）
ax_fft.grid(True)

# グラフ同士が重ならないようにレイアウトを自動調整
plt.tight_layout()

print("観測を開始します。終了する場合はグラフのウィンドウを閉じるか、Ctrl+Cを押してください。")

try:
    while True:
        # 音声データの読み込み
        data = stream.read(CHUNK, exception_on_overflow=False)
        audio_data = np.frombuffer(data, dtype=np.int16)
        
        # 波形グラフの更新
        line_wave.set_ydata(audio_data)
        
        # ハニングウィンドウをかけてノイズを減らす（FFTの定石）
        window = np.hanning(len(audio_data))
        
        # FFTの計算
        fft_data = np.abs(np.fft.rfft(audio_data * window)) / (CHUNK / 2)
        
        # FFTグラフの更新
        line_fft.set_ydata(fft_data)
        
        # 描画の更新
        fig.canvas.draw()
        fig.canvas.flush_events()

except KeyboardInterrupt:
    print("観測を終了します。")

finally:
    # 終了処理
    stream.stop_stream()
    stream.close()
    p.terminate()
```
