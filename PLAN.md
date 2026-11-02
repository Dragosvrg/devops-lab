# Planul DevOps pas cu pas

O sesiune pe zi, 45 de minute. Ritm: incalzire (intrebarea de la sesiunea anterioara, din memorie), pasi, "Gata cand", apoi explic cu vorbele mele.
Pasii marcati **Ghiceste** se fac inainte de rulare: prezic rezultatul, apoi verific.
Sesiunile de recapitulare amestecata: intrebari din toate etapele de dinainte.

# Fundatie (obligatoriu)

## Setup

### Sesiunea 1: Pregatesti laptopul
Material: github.com (https://github.com/signup)

Pasi:
- Ai cont pe github.com.
- Daca ai Windows: PowerShell ca Administrator, `wsl --install`, restart.
- Deschizi Ubuntu din Start si iti alegi user si parola.
- `sudo apt update && sudo apt install -y git`

Gata cand: `git --version` afiseaza o versiune.

Explica la final: Ce e WSL si de ce il folosesti pentru DevOps?
Raspuns de referinta: Un Linux real care ruleaza in Windows. Tot DevOps-ul e pe Linux, iar Docker Desktop foloseste WSL pe dedesubt.

## Git

### Sesiunea 2: Primele 4 nivele Git
Material: learngitbranching.js.org (https://learngitbranching.js.org)

Pasi:
- Tabul Main, sectiunea "Introduction Sequence".
- Faci toate cele 4 nivele, in ordine.
- La fiecare nivel, inainte sa tastezi, spui in gand ce o sa se intample cu desenul.

Gata cand: 4 bife verzi la Introduction Sequence.

Explica la final: Ce e un commit?
Raspuns de referinta: O versiune salvata a fisierelor, cu un mesaj, in istoricul local. Ca un snapshot la care te poti intoarce oricand.

### Sesiunea 3: Ramping Up
Material: learngitbranching.js.org (https://learngitbranching.js.org)

Pasi:
- Tabul Main, sectiunea "Ramping Up", toate 4 nivelele.
- Butonul de hint din joc il apesi maxim o data pe nivel.

Gata cand: Ramping Up e verde.

Explica la final: Ce e HEAD?
Raspuns de referinta: Pointerul la commit-ul pe care stai acum. Cand faci commit, HEAD avanseaza.

### Sesiunea 4: Moving Work Around
Material: learngitbranching.js.org (https://learngitbranching.js.org)

Pasi:
- Main > "Moving Work Around" (2 nivele).
- Primele 2 nivele din "A Mixed Bag".

Gata cand: 4 nivele noi bifate.

Explica la final: Ce face git cherry-pick?
Raspuns de referinta: Copiaza un commit anume de pe alt branch pe branch-ul curent.

### Sesiunea 5: Termini A Mixed Bag
Material: learngitbranching.js.org (https://learngitbranching.js.org)

Pasi:
- Restul nivelelor din "A Mixed Bag".
- Sari peste "Advanced Topics".

Gata cand: A Mixed Bag e verde.

Explica la final: Diferenta dintre merge si rebase?
Raspuns de referinta: Merge imbina doua branch-uri si pastreaza ambele istorii, cu un commit de imbinare. Rebase muta commit-urile tale peste celalalt branch, istoricul iese liniar.

### Sesiunea 6: Legi laptopul de GitHub
Material: GitHub > SSH keys (https://github.com/settings/keys)

Pasi:
- `git config --global user.name` si `user.email`.
- `ssh-keygen -t ed25519`, Enter la tot.
- `cat ~/.ssh/id_ed25519.pub`, copiezi linia.
- Pe GitHub: New SSH key, tip Authentication Key.
- `ssh -T git@github.com`

Gata cand: Mesajul "successfully authenticated".

Explica la final: Care cheie o pui pe GitHub si care nu pleaca niciodata de pe laptop?
Raspuns de referinta: Cea .pub (publica) merge pe GitHub. Cea fara .pub e privata si ramane doar la tine.

### Sesiunea 7: Primul script in devops-lab
Material: github.com/new (https://github.com/new)

Pasi:
- Repo `devops-lab` clonat in `~` (daca il ai deja, sari pasul).
- Creezi `healthcheck.sh` care afiseaza `date`, `uptime` si `df -h`.
- `chmod +x healthcheck.sh` si il rulezi.
- **Ghiceste:** ce o sa arate `git status` acum? Apoi rulezi si verifici.
- `git add`, `git commit -m "primul script"`, `git push`.

Gata cand: Vezi healthcheck.sh pe GitHub.

Explica la final: Ordinea comenzilor ca o modificare sa ajunga pe GitHub si ce face fiecare?
Raspuns de referinta: git add pune in stage, git commit salveaza versiunea local, git push o trimite pe GitHub.

### Sesiunea 8: Primul Pull Request

Pasi:
- `git checkout -b adauga-memorie`
- Adaugi in script o linie cu `free -h`.
- `git add .`, `git commit`, `git push -u origin adauga-memorie`
- Pe GitHub: Compare & pull request, apoi Merge pull request.
- **Ghiceste:** dupa merge pe GitHub, are main-ul de pe laptop linia noua? Verifici cu `git checkout main` si `cat healthcheck.sh`.
- `git pull`, apoi te uiti din nou.

Gata cand: Main-ul local are linia cu free -h.

Explica la final: De ce lucrezi pe branch cu PR in loc de push direct pe main?
Raspuns de referinta: Ca schimbarea sa fie verificata inainte sa intre. E un change request aprobat, nu o modificare direct in productie.

### Sesiunea 9: Recapitulare Git (recapitulare amestecata)
Material: learngitbranching.js.org (https://learngitbranching.js.org)

Pasi:
- Raspunzi la intrebarile de mai jos din memorie.
- Pe learngitbranching: tabul "Remote", primele 3 nivele din "Push & Pull".
- Fara notite: branch nou, modificare, PR, merge.

Gata cand: Faci un PR cap-coada fara sa te uiti.

Explica la final: Ce face git pull?
Raspuns de referinta: Aduce commit-urile noi de pe GitHub si le imbina in branch-ul local. E fetch plus merge.

## Docker

### Sesiunea 10: Instalezi Docker
Material: docs.docker.com (https://docs.docker.com/desktop/setup/install/windows-install/)

Pasi:
- Docker Desktop instalat, cu WSL 2.
- Settings > Resources > WSL integration: Ubuntu bifat.
- `docker run hello-world`

Gata cand: "Hello from Docker!".

Explica la final: Ce s-a intamplat, pas cu pas, cand ai rulat docker run hello-world?
Raspuns de referinta: Docker a cautat imaginea local, n-a gasit-o, a descarcat-o de pe Docker Hub, a pornit un container din ea si ti-a aratat ce a afisat.

### Sesiunea 11: Video Docker, partea 1
Material: YouTube: TechWorld with Nana (https://www.youtube.com/results?search_query=TechWorld+with+Nana+Docker+Tutorial+for+Beginners+full+course)

Pasi:
- "Docker Tutorial for Beginners" de TechWorld with Nana, cursul lung.
- 35 de minute, la 1.25x.
- Notezi minutul unde te-ai oprit.

Gata cand: Poti explica imagine vs container.

Explica la final: Diferenta dintre imagine si container?
Raspuns de referinta: Imaginea e sablonul, read-only. Containerul e o instanta pornita din ea, ca un proces pornit dintr-un executabil.

### Sesiunea 12: Primul container real

Pasi:
- `docker run -d -p 8080:80 --name web nginx`
- Deschizi `localhost:8080`.
- `docker ps`, apoi `docker logs web` dupa cateva refresh-uri.
- **Ghiceste:** ce vezi la localhost:8080 dupa `docker stop web`? Apoi verifici.
- `docker rm web`

Gata cand: Ai vazut pagina nginx, apoi ai oprit containerul.

Explica la final: Ce inseamna -p 8080:80?
Raspuns de referinta: Portul 8080 de pe laptop trimite traficul spre portul 80 din container. Ca un port forwarding.

### Sesiunea 13: Video Docker, partea 2
Material: YouTube: TechWorld with Nana (https://www.youtube.com/results?search_query=TechWorld+with+Nana+Docker+Tutorial+for+Beginners+full+course)

Pasi:
- Continui 35 de minute de unde ai ramas.
- Tastezi orice comanda din video.

Gata cand: Ai notat noul minut.

Explica la final: Ce se intampla cu datele scrise intr-un container cand il stergi?
Raspuns de referinta: Se pierd, daca nu sunt salvate pe un volum.

### Sesiunea 14: Intri intr-un container

Pasi:
- `docker run -d --name web nginx`
- `docker exec -it web bash`. Te uiti in `/etc/nginx`. `exit`.
- `mkdir site && echo salut > site/index.html`
- **Ghiceste:** ce o sa arate pagina cu folderul montat? Apoi: `docker run -d -p 8081:80 -v $(pwd)/site:/usr/share/nginx/html nginx`
- Deschizi `localhost:8081`. Opresti si stergi containerele.

Gata cand: "salut" in browser, servit din folderul tau.

Explica la final: La ce foloseste -v?
Raspuns de referinta: Monteaza un folder de pe laptop in container. Datele raman si dupa ce stergi containerul.

### Sesiunea 15: Primul tau Dockerfile

Pasi:
- In `devops-lab`, un `Dockerfile` cu: `FROM ubuntu:24.04`, `COPY healthcheck.sh /app/`, `RUN chmod +x /app/healthcheck.sh`, `CMD ["/app/healthcheck.sh"]`
- **Ghiceste:** care linie ruleaza la build si care la pornirea containerului?
- `docker build -t healthcheck .`
- `docker run --rm healthcheck`
- Commit si push.

Gata cand: Scriptul ruleaza din containerul tau.

Explica la final: Ce face fiecare: FROM, COPY, RUN, CMD?
Raspuns de referinta: FROM alege imaginea de baza. COPY pune fisiere in ea. RUN executa o comanda la build. CMD ruleaza cand porneste containerul.

### Sesiunea 16: Video Docker, partea 3
Material: YouTube: TechWorld with Nana (https://www.youtube.com/results?search_query=TechWorld+with+Nana+Docker+Tutorial+for+Beginners+full+course)

Pasi:
- Continui pana termini partea de Docker Compose.
- Daca nu ajungi azi, continui maine aceeasi sesiune.

Gata cand: Stii la ce foloseste docker-compose.yml.

Explica la final: Ce problema rezolva Docker Compose?
Raspuns de referinta: Pornesti mai multe containere legate intre ele dintr-un singur fisier, cu o singura comanda.

### Sesiunea 17: Docker Compose
Material: docs.docker.com (https://docs.docker.com/compose/gettingstarted/)

Pasi:
- `docker-compose.yml` cu `nginx` pe 8080 si `postgres` cu `POSTGRES_PASSWORD`.
- `docker compose up -d`, `docker compose ps`.
- `docker compose logs postgres`.
- `docker compose down`. Commit si push.

Gata cand: Ambele servicii Up.

Explica la final: Cum se gasesc serviciile intre ele intr-un compose?
Raspuns de referinta: Dupa numele serviciului, folosit ca hostname. Nginx ajunge la baza de date la adresa postgres.

### Sesiunea 18: Recapitulare amestecata (recapitulare amestecata)

Pasi:
- Raspunzi la intrebarile de mai jos din memorie.
- `docker system prune -a` (sterge imaginile si containerele de pe laptop).
- Refaci totul doar din repo: `docker build`, `docker compose up -d`.

Gata cand: Ai refacut totul fara notite.

Explica la final: Cum refaci tot mediul daca ai sters tot de pe laptop?
Raspuns de referinta: Clonezi repo-ul si rulezi build si compose. Tot ce trebuie e in fisiere, nu in capul tau. Asta e ideea.

## CI/CD

### Sesiunea 19: Primul workflow GitHub Actions
Material: docs.github.com/actions (https://docs.github.com/en/actions)

Pasi:
- Deschizi "Quickstart for GitHub Actions".
- Faci `.github/workflows/ci.yml` cu exemplul lor.
- Push si deschizi tabul Actions.

Gata cand: Un run verde in Actions.

Explica la final: Unde stau workflow-urile si ce le porneste?
Raspuns de referinta: In .github/workflows, ca fisiere YAML. Le pornesc evenimente ca push sau pull_request.

### Sesiunea 20: Verificare automata a scripturilor

Pasi:
- `ci.yml` ruleaza `shellcheck *.sh` la fiecare push.
- Push, te uiti in Actions.
- Daca e rosu, citesti eroarea si repari.

Gata cand: Shellcheck e verde.

Explica la final: Ce e CI, cu vorbele tale?
Raspuns de referinta: Verificare automata la fiecare modificare, ca erorile sa fie prinse inainte sa intre pe main.

### Sesiunea 21: Il strici intentionat

Pasi:
- Branch nou, pui in script `echo $HOME/$1` fara ghilimele.
- **Ghiceste:** trece sau pica CI-ul? De ce?
- Push, deschizi PR, verifici.
- Repari, push, verde, merge.

Gata cand: Rosu pe PR, apoi verde dupa fix.

Explica la final: Ce vede colegul pe PR cand CI-ul pica?
Raspuns de referinta: Un X rosu langa check. Nu se da merge pana nu e verde.

### Sesiunea 22: Build Docker automat

Pasi:
- In `ci.yml` adaugi pasul `docker build -t healthcheck .`
- Push, verifici pasul in Actions.
- Deschizi logul si gasesti liniile de build.

Gata cand: La fiecare push se construieste imaginea.

Explica la final: Pe ce masina ruleaza build-ul din Actions?
Raspuns de referinta: Pe un runner: o masina virtuala temporara de la GitHub, stearsa dupa job. Nu pe laptopul tau.

### Sesiunea 23: Nimic stricat nu intra pe main

Pasi:
- Settings > Branches (sau Rules): regula pentru `main`.
- Ceri PR si status checks verzi.
- Testezi cu un PR cu eroare.

Gata cand: Merge blocat cand CI e rosu.

Explica la final: Ce ai protejat si de ce conteaza in productie?
Raspuns de referinta: Main nu mai accepta nimic fara PR si CI verde. Nimic netestat nu ajunge mai departe.

### Sesiunea 24: Recapitulare amestecata (recapitulare amestecata)

Pasi:
- Raspunzi la intrebarile de mai jos din memorie.
- Fara notite: branch nou, modifici Dockerfile-ul, PR, astepti CI, merge.

Gata cand: Un ciclu complet fara sa te uiti.

Explica la final: Descrie drumul unei modificari de la laptop pana pe main.
Raspuns de referinta: Branch, commit, push, PR, CI ruleaza automat, verde, merge pe main.

## Terraform

### Sesiunea 25: Instalezi Terraform
Material: developer.hashicorp.com (https://developer.hashicorp.com/terraform/install)

Pasi:
- Pasii pentru Linux, Ubuntu/Debian, in WSL.
- `terraform -version`

Gata cand: Terraform afiseaza o versiune.

Explica la final: Ce inseamna infrastructure as code?
Raspuns de referinta: Infrastructura descrisa in fisiere text, tinute in git, si creata de un tool. Nu din click-uri.

### Sesiunea 26: Tutorial: Build
Material: HashiCorp: Get Started, Docker (https://developer.hashicorp.com/terraform/tutorials/docker-get-started)

Pasi:
- Seria "Get Started - Docker", tutorialul de build.
- **Ghiceste:** Inainte de apply, citesti `terraform plan` si spui ce o sa creeze.
- `terraform apply`.

Gata cand: Un nginx pornit de Terraform.

Explica la final: Ce face terraform plan si de ce il citesti?
Raspuns de referinta: Arata ce va crea, schimba sau sterge, fara sa faca nimic. E dry run-ul de dinainte de change.

### Sesiunea 27: Tutorial: Change si Destroy
Material: HashiCorp: Get Started, Docker (https://developer.hashicorp.com/terraform/tutorials/docker-get-started)

Pasi:
- Urmatoarele doua tutoriale din serie.
- **Ghiceste:** La fiecare plan, ghicesti inainte daca o sa scrie update sau replace.
- Citesti planul inainte de yes.

Gata cand: `docker ps` gol dupa destroy.

Explica la final: Ce e fisierul de state?
Raspuns de referinta: Memoria Terraform: ce a creat si cum arata. Pe baza lui calculeaza diferentele la fiecare plan.

### Sesiunea 28: Tutorial: Variables si Outputs
Material: HashiCorp: Get Started, Docker (https://developer.hashicorp.com/terraform/tutorials/docker-get-started)

Pasi:
- Ultimele tutoriale din serie.
- `terraform destroy` la final.

Gata cand: Seria Docker terminata.

Explica la final: De ce variabile in loc de valori scrise direct?
Raspuns de referinta: Acelasi cod merge pe medii diferite, test sau prod. Schimbi doar valorile.

### Sesiunea 29: Terraform in repo-ul tau

Pasi:
- `terraform/main.tf` care porneste nginx.
- `.gitignore`: `.terraform/`, `*.tfstate`, `*.tfstate.backup`.
- init, plan, apply, verifici, destroy.
- Commit si push.

Gata cand: Folderul terraform pe GitHub, fara state.

Explica la final: De ce .tfstate nu ajunge pe GitHub?
Raspuns de referinta: Poate contine date sensibile si e starea curenta. In echipa se tine intr-un backend remote, nu in git.

### Sesiunea 30: Terraform verificat in CI
Material: hashicorp/setup-terraform (https://github.com/hashicorp/setup-terraform)

Pasi:
- Job nou in CI cu `hashicorp/setup-terraform`.
- Pasi: `terraform init -backend=false`, `fmt -check`, `validate`.
- Push, verde.

Gata cand: Jobul de Terraform verde.

Explica la final: Ce verifica fmt si validate?
Raspuns de referinta: fmt verifica formatarea codului. validate verifica ca sintaxa si configuratia sunt corecte.

### Sesiunea 31: Recapitulare amestecata (recapitulare amestecata)

Pasi:
- Raspunzi la intrebarile de mai jos din memorie.
- Fara notite: schimbi portul nginx in Terraform, plan, apply, verifici, destroy.

Gata cand: Ai facut schimbarea citind singur planul.

Explica la final: Ce faci intai cand primesti un plan care zice "destroy" la ceva ce nu voiai?
Raspuns de referinta: Nu scrii yes. Citesti ce resursa e si de ce, si corectezi codul inainte.

## AWS

### Sesiunea 32: Cont AWS in siguranta
Material: aws.amazon.com/free (https://aws.amazon.com/free/)

Pasi:
- Cont AWS Free Tier.
- MFA pe root.
- Billing > Budgets: 1 USD, alerta pe email.
- Nimic altceva azi.

Gata cand: Bugetul apare si MFA e activ.

Explica la final: Primele doua lucruri intr-un cont AWS nou?
Raspuns de referinta: MFA pe root si un buget cu alerta, ca sa nu ai surprize la factura.

### Sesiunea 33: Curs AWS: IAM
Material: Udemy: Stephane Maarek (https://www.udemy.com/courses/search/?q=Ultimate+AWS+Certified+Solutions+Architect+Associate+Stephane+Maarek)

Pasi:
- Cursul "Ultimate AWS Certified Solutions Architect Associate", la reducere.
- Sari peste intro si creare cont.
- Sectiunea IAM, faci ce face el.

Gata cand: Stii user, group, role, policy.

Explica la final: User vs role?
Raspuns de referinta: User e o identitate permanenta pentru o persoana. Role e o identitate temporara, preluata de cineva sau de un serviciu.

### Sesiunea 34: User IAM pentru tine
Material: consola IAM (https://console.aws.amazon.com/iam/)

Pasi:
- User cu acces la consola, `AdministratorAccess`.
- MFA pe el.
- Te deloghezi de pe root si intri cu userul nou.

Gata cand: Logat cu userul IAM.

Explica la final: De ce nu lucrezi pe root?
Raspuns de referinta: Root are acces total si nu poate fi limitat. Exact ca pe un server: nu lucrezi ca root.

### Sesiunea 35: Curs AWS: EC2
Material: Udemy: Stephane Maarek (https://www.udemy.com/courses/search/?q=Ultimate+AWS+Certified+Solutions+Architect+Associate+Stephane+Maarek)

Pasi:
- Sectiunea EC2 basics.
- Te uiti, nu creezi instante odata cu el.

Gata cand: Stii AMI, instance type, security group.

Explica la final: Ce e un AMI?
Raspuns de referinta: Imaginea de disc din care porneste instanta. Ca o imagine Docker, dar pentru un server intreg.

### Sesiunea 36: Primul server EC2
Material: consola EC2 (https://console.aws.amazon.com/ec2/)

Pasi:
- Launch instance: Ubuntu, "Free tier eligible".
- Key pair, salvezi .pem.
- Security group: SSH doar de la My IP.
- **Ghiceste:** merge SSH de pe alt IP? De ce?
- `ssh -i cheia.pem ubuntu@IP`, rulezi healthcheck.sh.
- Terminate. Obligatoriu.

Gata cand: Script rulat pe EC2, instanta Terminated.

Explica la final: Ce e un security group?
Raspuns de referinta: Firewall-ul instantei. Spune ce trafic are voie sa intre si sa iasa.

### Sesiunea 37: AWS din linia de comanda
Material: docs.aws.amazon.com (https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

Pasi:
- AWS CLI v2 in WSL.
- Access key pentru userul tau (tip CLI).
- `aws configure`, regiunea `eu-central-1`.
- `aws sts get-caller-identity`

Gata cand: Comanda iti arata userul IAM.

Explica la final: Unde stau cheile din aws configure si de ce nu ajung in git?
Raspuns de referinta: In ~/.aws/credentials. Cine le are, are acces la contul tau si poate cheltui pe banii tai.

### Sesiunea 38: Tutorial: EC2 cu Terraform
Material: HashiCorp: Get Started, AWS (https://developer.hashicorp.com/terraform/tutorials/aws-get-started)

Pasi:
- Tutorialul de build din seria AWS.
- Verifici instanta in consola.
- **Ghiceste:** daca o stergi din consola, ce zice `terraform plan`? Incerci.
- `terraform destroy`.

Gata cand: Un EC2 creat si sters doar din cod.

Explica la final: Ce face Terraform daca cineva sterge manual o resursa?
Raspuns de referinta: La plan vede ca lipseste fata de state si propune s-o creeze din nou.

### Sesiunea 39: Serverul tau, din cod

Pasi:
- `terraform-aws/`: EC2 + security group (SSH de la IP-ul tau, port 80).
- `user_data` care instaleaza Docker si porneste nginx.
- apply, IP-ul public in browser.
- destroy. Commit si push.

Gata cand: nginx pe IP public, apoi distrus tot.

Explica la final: Ce e user_data?
Raspuns de referinta: Un script care ruleaza o singura data, la prima pornire a instantei.

### Sesiunea 40: Reteaua in AWS
Material: consola VPC (https://console.aws.amazon.com/vpcconsole/)

Pasi:
- Te uiti la: VPCs, Subnets, Route tables, Internet gateways.
- In README, 5 randuri: ce face fiecare.
- Comparatie: VPC = reteaua datacenter-ului, subnet = VLAN, security group = firewall.

Gata cand: README-ul are sectiunea de retea.

Explica la final: Subnet public vs privat?
Raspuns de referinta: Cel public are ruta spre internet gateway. Cel privat nu iese direct pe internet.

### Sesiunea 41: Recapitulare amestecata (recapitulare amestecata)
Material: consola Billing (https://console.aws.amazon.com/billing/)

Pasi:
- Raspunzi la intrebarile de mai jos din memorie.
- apply pe proiectul tau, verifici, destroy.
- Billing: costuri 0. EC2: nicio instanta sau volum ramas.

Gata cand: Factura 0, nimic pornit.

Explica la final: Ce verifici la finalul oricarei sesiuni de AWS?
Raspuns de referinta: Ca n-ai lasat nimic pornit (instante, volume, IP-uri) si ca factura e 0.

## Kubernetes

### Sesiunea 42: Kubernetes pe laptop
Material: minikube.sigs.k8s.io (https://minikube.sigs.k8s.io/docs/start/)

Pasi:
- minikube pentru Linux.
- kubectl.
- `minikube start`, `kubectl get nodes`.

Gata cand: Un nod Ready.

Explica la final: Ce e un nod?
Raspuns de referinta: O masina pe care ruleaza containerele. Aici, masina virtuala facuta de minikube.

### Sesiunea 43: Video Kubernetes, partea 1
Material: YouTube: TechWorld with Nana (https://www.youtube.com/results?search_query=TechWorld+with+Nana+Kubernetes+Tutorial+for+Beginners)

Pasi:
- "Kubernetes Tutorial for Beginners" de TechWorld with Nana.
- 40 de minute: Pod, Service, Deployment.
- Notezi minutul.

Gata cand: Stii Pod si Deployment.

Explica la final: Pod vs Deployment?
Raspuns de referinta: Pod-ul e unul sau mai multe containere rulate impreuna. Deployment-ul tine numarul dorit de poduri si le inlocuieste cand cad.

### Sesiunea 44: Il vezi cum se repara singur

Pasi:
- `kubectl create deployment web --image=nginx`
- `kubectl get pods`, copiezi numele.
- **Ghiceste:** ce se intampla dupa ce stergi podul?
- `kubectl delete pod NUMELE`, apoi imediat `kubectl get pods`.

Gata cand: Un pod nou, aparut singur.

Explica la final: De ce a aparut un pod nou cand l-ai sters?
Raspuns de referinta: Deployment-ul a vazut mai putine poduri decat a cerut si a pornit altul. Ce faci tu manual la o alerta, facut automat.

### Sesiunea 45: Video Kubernetes, partea 2
Material: YouTube: TechWorld with Nana (https://www.youtube.com/results?search_query=TechWorld+with+Nana+Kubernetes+Tutorial+for+Beginners)

Pasi:
- Partea cu fisiere YAML.
- Tastezi exemplele.

Gata cand: Intelegi un YAML de Deployment.

Explica la final: Ce sectiuni are un YAML de Deployment?
Raspuns de referinta: apiVersion, kind, metadata si spec, cu replici, selector si template-ul cu containerele.

### Sesiunea 46: Aplicatia in YAML

Pasi:
- `k8s/deployment.yaml` cu nginx, `replicas: 3`.
- `k8s/service.yaml`, tip NodePort.
- `kubectl apply -f k8s/`, `kubectl get pods`.
- `minikube service NUMELE`.
- Commit si push.

Gata cand: 3 poduri Running, pagina deschisa.

Explica la final: La ce foloseste un Service?
Raspuns de referinta: Da o adresa stabila unui grup de poduri care apar si dispar.

### Sesiunea 47: Imaginea ta in Kubernetes

Pasi:
- `minikube image load healthcheck`
- Deployment cu imaginea ta si `imagePullPolicy: Never`.
- **Ghiceste:** ce scrie podul daca scoti imagePullPolicy?
- `kubectl logs` pe podul tau.

Gata cand: Scriptul tau ruleaza in Kubernetes.

Explica la final: De ce imagePullPolicy: Never?
Raspuns de referinta: Imaginea e doar local in minikube, nu pe un registry. Fara asta, Kubernetes ar incerca s-o descarce si ar pica.

### Sesiunea 48: Scale si rollback

Pasi:
- `kubectl scale deployment web --replicas=5`
- `kubectl set image deployment/web nginx=nginx:1.27`
- `kubectl rollout status deployment/web`
- `kubectl rollout undo deployment/web`

Gata cand: Un update si un rollback.

Explica la final: Ce face kubectl rollout undo?
Raspuns de referinta: Readuce deployment-ul la versiunea anterioara. Rollback-ul la un deploy prost, intr-o comanda.

### Sesiunea 49: Recapitulare amestecata (recapitulare amestecata)

Pasi:
- Raspunzi la intrebarile de mai jos din memorie.
- Fara notite: deployment cu 2 replici din YAML, service, scale la 4, rollback.

Gata cand: Totul facut fara sa te uiti.

Explica la final: Leaga toate etapele: ce face fiecare tool in drumul codului pana ruleaza?
Raspuns de referinta: Git tine codul, Actions il verifica si construieste imaginea Docker, Terraform face serverele in AWS, Kubernetes ruleaza si repara containerele.

## Final

### Sesiunea 50: Portofoliul
Material: github.com (https://github.com/)

Pasi:
- README in `devops-lab`: 2-3 randuri pe etapa.
- Comenzile principale, ca oricine sa-l poata rula.
- Link la repo pe LinkedIn la Featured si in CV.
- In Claude Code: comanda "interviu".

Gata cand: Repo-ul arata ca un proiect.

Explica la final: Explica in 60 de secunde, in engleza, ce ai construit in devops-lab.
Raspuns de referinta: Nu are raspuns fix. Il exersezi pana iese fluent, cu comanda interviu in Claude Code.

# Bonus (dupa ce termin fundatia)

## Monitoring

### Sesiunea 51: Prometheus si Grafana
Material: prometheus.io (https://prometheus.io/docs/introduction/first_steps/)

Pasi:
- `monitoring/docker-compose.yml`: `prom/prometheus` (9090), `grafana/grafana` (3000), `prom/node-exporter` (9100).
- `prometheus.yml` care colecteaza de la `node-exporter:9100`.
- `docker compose up -d`
- `localhost:9090`, Status > Targets.

Gata cand: node-exporter UP.

Explica la final: Cum ia Prometheus metricile?
Raspuns de referinta: Le trage singur, periodic, de la fiecare target (scrape). Targeturile nu trimit nimic.

### Sesiunea 52: Dashboard in Grafana
Material: Node Exporter Full (https://grafana.com/grafana/dashboards/1860-node-exporter-full/)

Pasi:
- `localhost:3000`, admin / admin.
- Data source Prometheus: `http://prometheus:9090`.
- Dashboards > Import, ID `1860`.

Gata cand: Grafice CPU, memorie, disc.

Explica la final: Ce e un exporter?
Raspuns de referinta: Un proces care expune metrici despre ceva, de exemplu serverul, intr-un format pe care Prometheus il citeste.

### Sesiunea 53: Prima ta alerta
Material: prometheus.io (https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/)

Pasi:
- `alerts.yml`: daca `up == 0` timp de 1 minut.
- O incarci la `rule_files`, repornesti Prometheus.
- **Ghiceste:** dupa cat timp devine Firing daca opresti node-exporter?
- `docker compose stop node-exporter`, te uiti la `localhost:9090/alerts`.

Gata cand: Alerta Firing, apoi revine.

Explica la final: De ce for: 1m in regula de alerta?
Raspuns de referinta: Ca sa nu alerteze la o cadere de cateva secunde. Taie alertele false.

## Ansible

### Sesiunea 54: Primul contact cu Ansible
Material: docs.ansible.com (https://docs.ansible.com/ansible/latest/getting_started/index.html)

Pasi:
- `sudo apt install -y ansible`
- `inventory.ini`: `localhost ansible_connection=local`
- `ansible all -i inventory.ini -m ping`
- `ansible all -i inventory.ini -m command -a "df -h"`

Gata cand: Ping-ul raspunde pong.

Explica la final: Ce e inventory-ul?
Raspuns de referinta: Lista de servere pe care lucreaza Ansible.

### Sesiunea 55: Playbook pe un server real

Pasi:
- EC2 pornit cu Terraform-ul tau.
- IP-ul in inventory, user `ubuntu`, cheia .pem.
- `playbook.yml`: instaleaza nginx, copiaza healthcheck.sh.
- **Ghiceste:** ce scrie la a doua rulare?
- Rulezi de doua ori, apoi `terraform destroy`.

Gata cand: A doua rulare: changed=0.

Explica la final: Ce inseamna idempotent?
Raspuns de referinta: Rulezi de oricate ori si rezultatul e acelasi. A doua oara nu mai schimba nimic.

## Helm

### Sesiunea 56: Imaginea ta pe un registry
Material: GitHub Container Registry (https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)

Pasi:
- Token GitHub (classic) cu `write:packages`. Il tii doar la tine.
- `docker login ghcr.io -u Dragosvrg`
- `docker tag healthcheck ghcr.io/dragosvrg/healthcheck:1.0`
- `docker push ghcr.io/dragosvrg/healthcheck:1.0`

Gata cand: Imaginea apare la Packages.

Explica la final: Ce e un registry?
Raspuns de referinta: Locul de unde serverele descarca imaginile Docker. Un repo, dar pentru imagini.

### Sesiunea 57: Push automat din CI
Material: docker/login-action (https://github.com/docker/login-action)

Pasi:
- `docker/login-action` cu `ghcr.io` si `secrets.GITHUB_TOKEN`.
- `permissions: packages: write`.
- Build + push doar pe main.

Gata cand: Dupa merge, apare singura o versiune noua.

Explica la final: De ce push la imagine doar de pe main?
Raspuns de referinta: Doar codul verificat si aprobat devine imagine folosita mai departe.

### Sesiunea 58: Deploy cu Helm
Material: helm.sh (https://helm.sh/docs/intro/quickstart/)

Pasi:
- Instalezi Helm.
- `helm create app`, te uiti in `values.yaml`.
- `helm install app ./app`
- `replicaCount` schimbat, `helm upgrade app ./app`.
- `helm rollback app 1`

Gata cand: install, upgrade, rollback.

Explica la final: Ce e un chart Helm?
Raspuns de referinta: Un pachet de fisiere Kubernetes cu valori configurabile, pe care il instalezi si il versionezi ca pe o aplicatie.

## Python

### Sesiunea 59: Scriptul tau in Python
Material: docs.python.org (https://docs.python.org/3/library/shutil.html#shutil.disk_usage)

Pasi:
- `healthcheck.py` cu `shutil.disk_usage("/")`, `os.getloadavg()`, `datetime.now()`.
- Acelasi output ca scriptul bash.

Gata cand: `python3 healthcheck.py` merge.

Explica la final: Cand alegi Python in loc de bash?
Raspuns de referinta: Cand logica devine complexa, cand vrei tratare clara a erorilor sau cand vorbesti cu API-uri.

### Sesiunea 60: Python care vorbeste cu AWS
Material: boto3 quickstart (https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html)

Pasi:
- `python3 -m venv venv && source venv/bin/activate`
- `pip install boto3`
- Script care listeaza instantele EC2 cu ID si stare.
- Rulezi cu si fara un EC2 pornit.

Gata cand: Scriptul arata instantele.

Explica la final: Ce e boto3?
Raspuns de referinta: Libraria Python oficiala pentru AWS.

## AWS+

### Sesiunea 61: Certificarea AWS
Material: aws.amazon.com/certification (https://aws.amazon.com/certification/certified-solutions-architect-associate/)

Pasi:
- Termini cursul, o sectiune pe sesiune (repeti sesiunea asta pana termini).
- Teste de practica pana iei constant peste 80%.
- Programezi examenul.

Gata cand: Examen programat.

Explica la final: Cand esti gata de examen?
Raspuns de referinta: Cand iei constant peste 80% la testele de practica, nu doar o data.
