# CLAWAR2023









\usepackage[ruled, lined, linesnumbered, commentsnumbered, longend]{algorithm2e}
\begin{algorithm}[!htb]
\scriptsize
\SetAlgorithmName{Pseudo-código}
\SetAlgoLined \\
\KwIn{$vel_d$: velocidade desejada; $cp_{max}$: comprimento de passo máximo; $freqP_{max}$: frequência de passo máxima; $freqP_{min}$: frequência de passo mínima.}
\KwOut{$cp$: comprimento do passo; $freqP$: frequência do passo.}
\BlankLine
%\SetKwFunction{FcalccpfreqPasso}{calc_cp_freq_Passo}
\SetKwFunction{FMain}{calc\_cp\_freqP}
\SetKwProg{Pn}{Function}{:}{\KwRet $cp,\;freqP$}
\Pn{\FMain{$vel_d$, $cp_{max}$, $freqP_{max}$, $freqP_{min}$}}{
\\
{\textcolor{blue}{\%Iniciação de variáveis.}}\\
$a \gets 1$;\\
$cp \gets cp_{max}$;\\
$freq_p \gets freqP_{max}$;\\
{\textcolor{blue}{\%Verifica se a velocidade desejada é maior que a velocidade  realizada com o comprimento máximo e frequência máxima.}}\\
\If{$vel_d > freqP_{max} \times cp_{max}$}{
$cp \gets cp_{max}$;\\
$freq_p \gets freqP_{max}$;
}
\Else{
{\textcolor{blue}{\%Inicia a busca da frequência e comprimento de passo que resolva $V_{mp} = d\,f_p$.}}\\
\While{$a=1$}{
{\textcolor{blue}{\%Verifica se encontrou uma frequência e comprimento de passo para a velocidade desejada.}}\\
\If{$vel_d \geq cp \, (freqP - freqP_{min})$ \textbf{and} $vel_d \leq cp \, freqP$}{
{\textcolor{blue}{\%Encontrou uma frequência e comprimento de passo para a velocidade desejada.}}\\
$freqP \gets freqP + 0.001$;\\
$cp \gets vel_d / freqP$;\\
$a \gets 0$;\\
{\textcolor{blue}{\%Finaliza a busca}}\\
\textbf{break};
}
\ElseIf{$freqP \leq freqP_{min}$}{
{\textcolor{blue}{\%Incrementa a o comprimento do passo se a varredura de frequência chegou na frequência mínima}}\\
$cp \gets cp + 0.005$;\\
$freqP \gets freqP_{max}$;\\
\If{$cp > cp_{max}$}{
$cp \gets 0$;
}
}
\Else{
{\textcolor{blue}{\%Decrementa a frequência de passo para a varredura }}\\
$freqP \gets freqP - 0.001$;
}
}
}
}
\BlankLine
\caption{Função para cálculo da frequência e comprimento de passo.}
\label{cod:calcCpFp}
\end{algorithm}
