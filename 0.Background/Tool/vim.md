# Paste Problem

vim的insert模式粘贴文本进入的时候，容易出现indent不规整的问题，解决方法：
1. enter normal mode.
2. :set paste
3. enter insert mode.
4. :set nopaste
5. :set pastetoggle=\<F3\>