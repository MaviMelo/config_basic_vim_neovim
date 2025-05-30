
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::

     Neovim é uma versão melhorada do Vim tradicional, que tem suporte nativo para Lua, linguagem de programação brasileira muito versátil, e gerenciadores de plugins modernos como Lazy.nvim, por exemplo. Porém o Vim ainda é o editor de texto que vem por padão em muitas distribuições de sistemas operacionais com base no kernel do Linux, apesar de que o NeoVim é estremamente facil de instalar no terminal (```bash: sudo apt install neovim).
     Muitos usuários de terminal com filosofias de trabalho minimalista e/ou que precisam trabalhar em ambientes alheios, onde não encontram suas configurações/setup de trabalho (computadores diferentes), muitas vezes procuram um editor de texto com uma configuração mínima de personalização de trabalho. Nesse caso se não quiser instalar e carregar toda uma configuração do NeoVim, ele precisa apenas criar o arquivo ' .vimrc ', com suas configurações de trabalho no diretório home (~/). 
    As configurações disponibilizadas aqui são testadas, básicas e customizáveis. Todavia é preciso garantir edição correta do código, observando o que é compativel e o que pode causar conflitos, principalmente no Vim que é mais antigo. 


    Para carregar essas configurações para o Vim e/ou NeoVim que já estão carregados com outras configurações, antes de mover os diretório .config/nvim (configurações para o NeoVim) e/ou o arquivo .vimrc (configurações para o Vim) para o diretório home ( ~/ ) no sistema  operacional é preciso limpar as configurações antigas para não haver coflitos.
 

Procedimento válido para: Linux; macOS (Unix); Windows via WSL (Windows Subsystem for Linux):

  0. Se o computador não é seu e já tem configurações para o Vim e/ou NeoVim:

     0.1 Apenas use o/s editor/es, simples.

     0.2 Se por algum motivo você precisa usar suas configurações, faça um backup das configurações atuais: crie um diretório (pasta) de nome backupvim, por exemplo, e copie o arquivo .vimrc (caminho até o arquivo: ~/.vimrc) e/ou a pasta nvim (caminho até o diretório: ~/.config/nvim) para dentro ela.

```bash:
	mkdir  ~/backupvim			           # cria o diretório. 

	cp -r -p  ~/.vimrc  ~/.config/nvim  ~/backupvim          # A opção -p mantém metadados (data
                                                            de modificação e permissões).

         0.3 Após termino do trabalho reinstale as configurações anteriores refazendo a etapa "1. Remover as configurações e dados..." e copie ou mova para ~/  (home) os backups feitos:

  ```bash:
    cd ~/backupvim
    cp -r -p  ~/.vimrc  ~/.config/nvim  ~/
    
1. Remover as configurações e dados antigos.

     1.1. Para o NeoVim (```bash: nvim)
```bash:

	# Configurações principais
	rm -rf ~/.config/nvim

	# Dados, plugins e caches
	rm -rf ~/.local/share/nvim 	# Plugins e dados instalados
	rm -rf ~/.cache/nvim        	# Arquivos temporários/cache
	rm -rf ~/.local/state/nvim  	# Estado da sessão (opcional)

	# Opcional: reinstale o neovim (se houver problemas com a intalação)

	sudo apt purge neovim && sudo apt install neovim 	# no Linux / WSL
	brew reinstall neovim 			# no macOS (via Homebrew)
 

    1.2. Para o Vim (```bash: vim)
```bash:

	# Remove a pasta de configurações e plugins
	rm -rf ~/.vim
	
	# Remove os arquivos de configuração
	rm ~/.vimrc ~/.gvimrc   	  # .vimrc (config principal) e .gvimrc (config GUI)
	
	# Opcional: Remove histórico e sessões salvas
	rm ~/.viminfo
	
	# Opcional: reinstale o vim (se houver problemas com a intalação)
	sudo apt purge vim && sudo apt install vim 	# no Linux (Debian/Ubuntu/WSL)
	brew reinstall vim 				# no macOS (via Homebrew)
    

2. ESTRUTURA DE ARQUIVOS (Linux/WSL/macOS):

2.1. Para Neovim:
   ~/
    └── .config/
        └── nvim/
            ├── init.vim              
            └── lua/
                └── config.lua    (configurações em Lua)


2.2. Para Vim tradicional:
   ~/
    └── .vimrc                  (configurações em VimScript)


3. APÓS INSTALAR:
    3.1. Vim(```bash: vim): Executar :PlugInstall
    3.2. Neovim(```bash: nvim): Executar :Lazy install
    3.3. Executar o arquivo setup.sh para instalações de dependencias para o correto funcionamento das configurações do Neovim.

```bash:
        sudo bash -x ~/.config/nvim/setup.sh     # necessário permissão root (administrador).

4. OBSERVAÇÕES SOBRE COMPATIBILIDADE:

  Versões mais antigas do Vim não tem integração com clipboard (copiar e colar com o ambiente externo do editor). Verifique a versão (```bash:   vim --version) e  procure por +clipboard ou +xterm_clipboard. Caso não tenha compatibilidade (-clipboard) é opcional usar outra versão do vim que tenha essa compatibilidade ainda que, nesse caso, faria mais sentido instalar/usar o NeoVim.
  Também é interesante resaltar que versões do NeoVim mais antigas  que a 'V0.10.0' tem uma dificuldade em ter um funcionamento satisfatório com mecanismos de lsp e linter, que  auxiliam na edição de código e mostrando os erros de sintaxe e lógica 

  Comandos para usar Vim com supote ao clipboard:

```bash

apt list --installed | grep vim     # Listar pacotes do Vim instalados

sudo apt purge vim                    # Remover o pacote (ex.: sudo apt purge <nome-do-pacote>)
    
sudo apt install vim-gtk3          # Instalar versão com suporte ao clipboard

:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::






## 🚀 Instalação

Clone o repositório e execute o script de instalação:

```bash:


git clone https://github.com/MaviMelo/config_basic_vim_neovim ~/.config/nvim

sudo bash -x .config/nvim/setup.sh   # necessário permissão root
