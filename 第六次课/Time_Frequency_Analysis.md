# <center>Time Frequency Analysis</center>

## <center>The  sixth lesson</center>

Time-frequency analysis is a method of analyzing **time-varying** signals. It is used to analyze **non-stationary** signals, which are signals whose frequency content changes over time. 

The Fourier Transform is not suitable for analyzing non-stationary signals because it assumes that the signal is stationary. The Short-Time Fourier Transform (STFT) is a method of analyzing non-stationary signals by applying the Fourier Transform to small windows of the signal.

**Knowledge that must be mastered**:

1. ***Fourier Transform***
For a continuous-time function $x(t)$ , the Fourier transform of $x(t)$ can be defined as:
\[
X(\omega) = \int_{-\infty}^{\infty} x(t) e^{-j{\omega}t} dt
\]
And the inverse Fourier transform of $X(\omega)$ is given by:
\[
x(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} X({\omega}) e^{j{\omega}t} d{\omega}
\]

2. ***Parseval’s Theorem of Fourier Transform***
Parseval’s theorem states that **the energy of signal $x(t)$ [ if $x(t)$ is aperiodic ]** or **power of signal $x(t)$ [ if $x(t)$ is periodic ]** in the time domain is equal to the energy or power in the frequency domain.
Therefore,if
\[x_1(t) \leftrightarrow X_1({\omega})\]\[x_2(t) \leftrightarrow X_2({\omega})\]
Then, Parseval’s theorem of Fourier transform states that:
$$
<x_1(t),x_2(t)> = \frac{1}{2\pi}<X_1({\omega}),X_2({\omega})>
$$
\[ \int_{-\infty}^{\infty} x_1(t)x_2^*(t) dt = \frac{1}{2\pi}\int_{-\infty}^{\infty} X_1({\omega})X_2^*({\omega}) d{\omega} \]
Where, $x_1(t)$ and $x_2(t)$ are complex functions.
Proof one:
\[
\int_{-\infty}^{\infty} x_1(t)x_2^*(t) dt = \int_{-\infty}^{\infty} \left( \frac{1}{2\pi} \int_{-\infty}^{\infty} X_1({\omega}) e^{j{\omega}t} d{\omega} \right) x_2^*(t) dt
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} X_1({\omega}) \left( \int_{-\infty}^{\infty} x_2^*(t) e^{j{\omega}t} dt \right) d{\omega}
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} X_1({\omega}) \left( \int_{-\infty}^{\infty} x_2(t) e^{-j{\omega}t} dt \right)^* d{\omega}
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} X_1({\omega})X_2^*({\omega}) d{\omega}
\]
Proof two:
\[
\frac{1}{2\pi} \int_{-\infty}^{\infty} X_1({\omega})X_2^*({\omega}) d{\omega} = \frac{1}{2\pi} \int_{-\infty}^{\infty} \left( \int_{-\infty}^{\infty} x_1(t) e^{-j{\omega}t} dt \right) X_2^*({\omega}) d{\omega}
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} \left( \int_{-\infty}^{\infty} x_1(t) e^{-j{\omega}t} dt \right) \left( \int_{-\infty}^{\infty} x_2(s) e^{-j{\omega}s} ds \right)^* d{\omega}
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x_1(t) x_2^*(s)  e^{-j{\omega}t} e^{j{\omega}s} dt ds d{\omega}
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x_1(t) x_2^*(s) \left( \int_{-\infty}^{\infty}  e^{-j{\omega}(t-s)} d{\omega} \right)  dt ds
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} x_1(t) x_2^*(s) 2\pi \delta(t-s) dt ds
\]
\[
= \int_{-\infty}^{\infty} x_1(t) x_2^*(t) dt
\]

1. ***Parseval’s Identity of Fourier Transform***
The Parseval’s identity of Fourier transform states that the energy content of the signal $x(t)$ is given by：
\[
E=\int_{-\infty}^{\infty} |x(t)|^2 dt = \frac{1}{2\pi} \int_{-\infty}^{\infty} |X({\omega})|^2 d{\omega}
\]

    - The Parseval’s identity is also called **energy theorem** or **Rayleigh’s energy theorem**
    - The quantity $|X({\omega})|^2$ is called the energy density spectrum of the signal $x(t)$

    Proof:
If $x_1(t)$ = $x_2(t)$ = $x(t)$ , then the energy of the signal is given by,
\[
E=\int_{-\infty}^{\infty} |x(t)|^2 dt = \int_{-\infty}^{\infty} x(t)x^*(t) dt
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} X({\omega})X^*({\omega}) d{\omega}
\]
\[
= \frac{1}{2\pi} \int_{-\infty}^{\infty} |X({\omega})|^2 d{\omega}
\]

1. ***Possion’s Summation Formula***
$g(t)$ is a periodic function with time period $T$.
\[g(t)= \sum_{n=-\infty}^{\infty} x(t+nT)\]
Then, the Fourier series of $g(t)$ is given by:
\[
g(t) = \sum_{n=-\infty}^{\infty} c_n e^{jnw_0t}
\]
Where, $c_n$ is the Fourier series coefficient of $g(t)$ and is given by:
\[
c_n = \frac{1}{T} \int_{T} g(t) e^{-jn{\omega}_0t} dt
\]
Where, ${\omega}_0 = \frac{2\pi}{T}$
\[g(t) = \sum_{n=-\infty}^{\infty} x(t+nT) = x(t) + x(t+T) + x(t+2T) + x(t+3T) + \cdots\]
Extract a period from the periodic pulse sequence, then perform a Fourier transform on it.
\[X({\omega}) = \int_{T} x(t) e^{-j{\omega}t} dt\]
\[c_n = \frac{1}{T} \int_{T} g(t) e^{-jn{\omega}_0t} dt\]
\[c_n = \frac{1}{T} \int_{T} (\sum_{n=-\infty}^{\infty} x(t+nT)) e^{-jn{\omega}_0t} dt\]
\[c_n = \frac{1}{T} \int_{T} x(t) e^{-jn{\omega}_0t} dt\]
\[c_n = \frac{1}{T} X({\omega})|_{n{\omega}_0}\]
\[c_n = \frac{1}{T} X(n{\omega}_0)\]
Where, $X({\omega})$ is the Fourier transform of $x(t)$
Therefore, Possion’s Summation Formula is given by:
**\[g(t) = \sum_{n=-\infty}^{\infty} x(t+nT) = \frac{1}{T} \sum_{n=-\infty}^{\infty}  X(n{\omega}_0) e^{jn{\omega}_0t}\]**
***Also, the other way to prove the Possion’s Summation Formula:***
\[g(t) = \sum_{n=-\infty}^{\infty} x(t+nT) = \sum_{n=-\infty}^{\infty} c_n e^{jn{\omega}_0t}\]
\[c_n = \frac{1}{T} \int_{T} g(t) e^{-jn{\omega}_0t} dt = \frac{1}{T} \int_{T} (\sum_{n=-\infty}^{\infty} x(t+nT)) e^{-jn{\omega}_0t} dt\]
\[ = \frac{1}{T} \sum_{n=-\infty}^{\infty} \int_{0}^{T} x(t+nT) e^{-jn{\omega}_0t} dt\]
\[ = \frac{1}{T} \sum_{n=-\infty}^{\infty} \int_{nT}^{(n+1)T} x(t^{'}) e^{-jn{\omega}_0(t^{'}-nT)} dt^{'}\]
\[ = \frac{1}{T}  \int_{-\infty}^{\infty} x(t^{'}) e^{-jn{\omega}_0t^{'}} dt^{'}\]
\[ = \frac{1}{T} X(n{\omega}_0)\]
\[g(t) = \sum_{n=-\infty}^{\infty} x(t+nT) = \frac{1}{T} \sum_{n=-\infty}^{\infty}  X(n{\omega}_0) e^{jn{\omega}_0t}\]
Where, $X({\omega})$ is the Fourier transform of $x(t)$
1. ***Sample for $y(t)$***
\[y_1(n) = y(t) \sum_{n=-\infty}^{\infty} \delta(t-nT)\]
Fourier Transform of $y(k)$ is given by:
\[Y_1({\omega}) = \frac{1}{2\pi} Y({\omega}) * (w_0 \sum_{n=-\infty}^{\infty} \delta({\omega}-n{\omega}_0))\]
\[Y_1({\omega}) = \frac{1}{T} \sum_{n=-\infty}^{\infty} Y({\omega}-n{\omega}_0)\]
where, ${\omega}_0 = \frac{2\pi}{T}$

1. ***Notation T、M***
    1. \[T_x(f(t)) = f(t-x)\]
    2. \[M_{\omega}(f(t)) = f(t) e^{j{\omega}t}\]
    3. \[T_xM_{\omega}(f(t)) = T_x(f(t) e^{j{\omega}t}) = f(t-x) e^{j{\omega}(t-x)}\]
    4. \[M_{\omega}T_x(f(t)) = M_{\omega}(f(t-x)) = f(t-x) e^{j{\omega}t}\]
    5. \[\mathcal{F}\ [T_xM_{{\omega}0}(f(t))] = \int_{-\infty}^{\infty} f(t-x) e^{j{\omega}_0(t-x)} e^{-j{\omega}t} dt = e^{-j{\omega}x} F({\omega}-{\omega}_0) = M_{-x}T_{\omega}{_0}(F({\omega}))\]