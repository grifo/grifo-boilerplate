# Grifo Boilerplate

Uma adaptação do projeto [HTML5 Boilerplate](http://html5boilerplate.com) usando [Less](http://lesscss.org) e mantendo [CSS reset](http://www.cssreset.com).
<br>
<br>
<br>
## CoffeeScript e Less
Temos um [Cakefile](http://coffeescript.org/documentation/docs/cake.html) pra agilizar nosso trabalho com [Less](http://lesscss.org) e [CoffeeScript](http://coffeescript.org).

### Requisitos 
* **Node**
* **CoffeeScript:** `sudo npm install coffee-script -g`
* **Less:** `sudo npm install less -g`	*Certifique-se que a Gem Ruby não esteja sendo chamada através de `lessc -v`.*
* **Uglifyjs:** `sudo npm install uglify-js -g`

### Configuração

`coffee.push 'main', 'base', '…'` arquivos .coffee

`less.push 'main', 'base', '…'` arquivos .less

`coffee.src = '_coffee/'` pasta origem dos arquivos .coffee

`coffee.dst = 'scripts/'` pasta destino

`coffee.compress = true'` comprimir o resultado com [UglifyJs](https://github.com/mishoo/UglifyJS)


`less.src = '_less/'` pasta origem dos arquivos .less

`less.dst = 'styles/'` pasta destino

`less.compress = true'` comprimir o resultado


``head = "`date -u +'%Y-%m-%d %H:%M GMT'`"`` assinatura no arquivo gerado

`tail = "\n  created by Grifo"`

### Como usar


	cake build
Compila os arquivos .coffee e .less das pastas `src` para as pastas `dst`.

	cake watch
Além de compilar, esta tarefa recompila os arquivos a cada nova alteração. Para Less, os arquivos incluídos por `@import` também disparam são assistidos e podem disparar recompilação.
<br>
<br>
<br>
## Favion
Pode ser gerado de acordo com este [Gist](https://gist.github.com/2870726).
<br>
<br>
<br>
## Plugins jQuery
Temos um repositório de plugins [Grifo-jquery-plugins](https://github.com/grifo/grifo-jquery-plugins) e mais alguma coisa neste [Gist](https://gist.github.com/2b6b1c1ca23351e74fa4).
<br>
<br>
<br>

	
  
                                  /T /I
                                   / |/ | .-~/
                               T\ Y  I  |/  /  _
              /T               | \I  |  I  Y.-~/
             I l   /I       T\ |  |  l  |  T  /
          T\ |  \ Y l  /T   | \I  l   \ `  l Y
      __  | \l   \l  \I l __l  l   \   `  _. |
      \ ~-l  `\   `\  \  \\ ~\  \   `. .-~   |
       \   ~-. "-.  `  \  ^._ ^. "-.  /  \   |
     .--~-._  ~-  `  _  ~-_.-"-." ._ /._ ." ./
      >--.  ~-.   ._  ~>-"    "\\   7   7   ]
     ^.___~"--._    ~-{  .-~ .  `\ Y . /    |
      <__ ~"-.  ~       /_/   \   \I  Y   : |
        ^-.__           ~(_/   \   >._:   | l______
            ^--.,___.-~"  /_/   !  `-.~"--l_ /     ~"-.
                   (_/ .  ~(   /'     "~"--,Y   -=b-. _)
                    (_/ .  \  :           / l      c"~o \
                     \ /    `.    .     .^   \_.-~"~--.  )
                      (_/ .   `  /     /       !       )/
                       / / _.   '.   .':      /        '
                       ~(_/ .   /    _  `  .-<_
                         /_/ . ' .-~" `.  / \  \          ,z=.
                         ~( /   '  :   | K   "-.~-.______//
                           "-,.    l   I/ \_    __{--->._(==.
                            //(     \  <    ~"~"     //
                           /'  \     \  \     ,v=.  ((
                         .^.    \     "  }__ //===-  `
                        / /      "-.,__ {---(==-       -Grifo
                      .^ '              "   ll       
                    .^ .^                    \\
                   (   /                          ~^
                    \/           

