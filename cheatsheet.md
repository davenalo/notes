vim

:h "keyword" - help
:sav "name" - save as
k - opens the man pages at the selected word

wW eE

bB ge gE <-- hacia atrás

0 - inicio de línea

$ - fin de línea

^ - primer caracter de la línea

S - último caracter de la línea

HML - high medium low de lo visible´

{ } - parágrafos

SS - primera línea del documento

% - siguiente mismo caracter

comentar las líneas:

ctrl + v -> arrows -> shift+i -> # -> ESC

descomentar:

ctrl + v -> arrows -> x -> ESC

---

tmux

bind: ctrl + a (por defecto ctrl + b) 

bind + $ - renombrar

bind + d - detach

tmux, tmux new, tmux new -s "name session"
tmux ls
bind + s

tmux kill-ses, tmux kill-session -t "name session"

tmux kill-session -a "name session" <--- cierra todas menos esa sesión

tmux a, tmux at, tmux attach (attach last session)

tmux -t, tmux at -t, tmux attach -t "name session"

bind + c - new window

bind + , - rename window

bind + & - close window



