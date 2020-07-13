# -*- mode: ruby -*-

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu1804"
  config.vm.provision "shell", privileged: false, inline: <<~SHELL
    sudo snap install emacs --beta --classic
    curl --silent -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
    export NVM_DIR="$HOME/.nvm"
    source "$NVM_DIR/nvm.sh"
    nvm install node
    npm install -g prettier
    emacs_d="$HOME/.emacs.d"
    mkdir -p $emacs_d
    cat > $emacs_d/init.el <<INIT_EL
      (require 'package)
      (add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)

      (package-initialize)
      (unless (package-installed-p 'use-package)
        (package-refresh-contents)
        (package-install 'use-package))

      (use-package prettier
        :ensure t
        :init
        (add-hook 'after-init-hook #'global-prettier-mode))

      (use-package markdown-mode
        :ensure t
        :commands (markdown-mode gfm-mode)
        :mode (("README\\.md\\'" . gfm-mode)
               ("\\.md\\'" . markdown-mode)
               ("\\.markdown\\'" . markdown-mode))
        :init (setq markdown-command "multimarkdown"))

      (setq inhibit-startup-screen t)
    INIT_EL
    touch $HOME/.hushlogin
    echo "exec emacs" >> $HOME/.bashrc
  SHELL
end
