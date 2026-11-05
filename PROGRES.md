# Progres

- 2026-11-02, Sesiunea 1 (Setup): facuta (WSL si git merg). Intrebarea de la final a primit raspuns la incalzire.
- 2026-11-02, Sesiunea 2 (Primele 4 nivele Git): terminata. Commit = snapshot cu mesaj in istoric (nu e branch). `add` alege ce intra in commit, `commit` il salveaza. `main` vs `origin/main` arata ce n-ai pushuit, nu ce e live.
- 2026-11-02, Sesiunea 3 (Ramping Up): nivelele facute. Am inteles HEAD detached (HEAD arata direct spre un commit, discul se aliniaza cu el), `HEAD^`/`HEAD~N` merg doar spre trecut. Intrebarea sesiunii ("Ce e HEAD?") a primit raspuns corect.
- 2026-11-04, Sesiunea 4 (Moving Work Around): terminata. `rebase -i` cere punct de start (ex. `HEAD~3`), commit-urile se refac automat dupa `:wq`. Orice commit cu parinte schimbat primeste hash nou, in lant. cherry-pick copiaza (nu muta) pe branch-ul curent.
- 2026-11-04, Sesiunea 5 (A Mixed Bag): terminata, plus Advanced Topics (extra). `switch` muta HEAD, `branch -f` muta eticheta branch-ului. Merge = commit nou cu 2 parinti; rebase = copii noi (X', Y') peste celalalt branch, istoric liniar.
- 2026-11-05, Sesiunea 6 (Legi laptopul de GitHub): terminata. Cheia ed25519 era deja facuta si pe GitHub, `ssh -T` = successfully authenticated. .pub merge pe GitHub (doar verifica), privata ramane pe laptop (semneaza). Cheie privata scapata = intai o revoci pe GitHub, apoi generezi alta.
- 2026-11-05, Sesiunea 7 (Primul script in devops-lab): terminata. `healthcheck.sh` (date, uptime, df -h) pe GitHub. add = stage, commit = local, push = GitHub; untracked vs modified; `restore --staged` scoate din stage; `sed -i` scrie in fisier. Un commit = o schimbare logica.
