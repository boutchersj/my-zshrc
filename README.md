# my-zshrc

alias edit_bash="open -e ~/.zshrc"
alias source_bash="source ~/.zshrc"

# Load Git completion
zstyle ':completion:*:*:git:*' script ~/.zsh/git-completion.bash
fpath=(~/.zsh $fpath)

autoload -Uz compinit && compinit

# Load version control information                                                                                          
autoload -Uz vcs_info                                                                                                      
precmd() { vcs_info }                                                                                                      

# Format the vcs_info_msg_0_ variable                                                                                      
zstyle ':vcs_info:git:*' formats '[%b]'                                                                                    

# Set up the prompt (with git branch name)                                                                                  
setopt PROMPT_SUBST                                                                                                        
PROMPT='${PWD/#$HOME/~} ${vcs_info_msg_0_} $ '

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
