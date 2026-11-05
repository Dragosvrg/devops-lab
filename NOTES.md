## 2026-11-05 | Recapitulare sesiunile 1-7

### Git de baza (S2)
- Commit = snapshot cu mesaj in istoric. NU e branch.
- `add` alege ce intra in commit (stage), `commit` salveaza LOCAL.
- `main` vs `origin/main` = ce n-ai pushuit inca. NU arata ce e live.

### HEAD (S3)
- HEAD = unde esti acum. De obicei arata spre un branch.
- HEAD detached = arata direct spre un commit, iar fisierele de pe disc se aliniaza cu el.
- `HEAD^` / `HEAD~3` = mergi doar inapoi in istoric.

### Mutat munca (S4)
- `rebase -i HEAD~3` = rearanjezi ultimele 3 commit-uri, se aplica dupa `:wq`.
- Parinte schimbat = hash nou, in lant pentru toate commit-urile de dupa.
- `cherry-pick` = COPIAZA un commit pe branch-ul curent (nu il muta).

### Merge vs rebase (S5)
- `switch` muta HEAD, `branch -f` muta eticheta branch-ului.
- Merge = commit nou cu 2 parinti, ambele istorii raman.
- Rebase = copii noi (X', Y') peste celalalt branch, istoric liniar. Ambele branch-uri raman.

### SSH (S6)
- `.pub` merge pe GitHub (doar verifica). Cheia privata ramane pe laptop (semneaza).
- Cheie privata scapata: 1) o stergi de pe GitHub (revoci), 2) generezi alta.
- Test: `ssh -T git@github.com` = "successfully authenticated".

### Primul script (S7)
- `#!/bin/bash` pe prima linie, `chmod +x` (sau 755), rulare cu `./script.sh`.
- `git status`: untracked = fisier nou | modified = deja in istoric, schimbat.
- `add` -> `commit` (local) -> `push` (GitHub).
- Un commit = o schimbare logica (revert curat).
- `sed 's/vechi/nou/' f` = afiseaza | `sed -i ...` = scrie in fisier. (flashcard)