# Acesso e VPS

Regras do servidor do coletivo. O objetivo é simples: ninguém quebra a máquina, nem por descuido, nem por maldade, e todo projeto tem onde viver.

## O modelo

O servidor pertence ao anfitrião. Cada projeto tem o próprio subdomínio e roda num container isolado. Ninguém além do anfitrião tem acesso ao sistema operacional.

Quem entrega código manda para o repositório e o deploy é combinado. Quem quer testar em casa roda o docker-compose local, sem depender de produção.

## Fortalecimento

- SSH só por chave, login por senha desativado.
- Firewall fechada por padrão: portas 22, 80 e 443.
- Traefik como proxy reverso, com certificado automático.
- CrowdSec ou fail2ban vigiando as portas.
- Uptime Kuma avisando quando algo cai.
- Container e banco separados por projeto, sem rede compartilhada.

## Segredos

Senhas e chaves ficam em arquivo de ambiente por serviço, fora do repositório e fora do chat. Segredo vazado em commit é trocado na hora e tratado como incidente.

## Backup

Snapshot periódico e cópia fora do servidor, com restic para B2. Monitoramento e backup são responsabilidade do anfitrião. O projeto não precisa cuidar disso.

## Quando a VPS fica pequena

O gatilho de troca é o coletivo, não um projeto único. Quando houver mais de um projeto ativo no servidor, sentamos e avaliamos uma máquina maior, com custo dividido de forma opcional e transparente. Não se espera o servidor estourar para conversar.