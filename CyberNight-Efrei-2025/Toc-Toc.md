# Challenge Toc Toc

## Infos dans le pdf procédures:

*Cible*: 10.44.10.144
*Protocole* : SSH (configuration par défaut, donc port 22)
*Une liste de ports spécifiques est donnée* : 7854, 1803, 4576.

Le titre fait référence au port knocking: https://fr.wikipedia.org/wiki/Port_knocking

## Protocole
Il faut donc "frapper" aux ports dans l'ordre indiqué par le document pour ouvrir temporairement le port SSH.
Séquence de Port Knocking :
- Port 7854
- Port 1803
- Port 4576

Identifiants :
  * Utilisateur : neuill 
  * Mot de passe : TurboNeuill


On utilise donc netcat pour etablir une connection à chaque port dans l'ordre (-z pour ne pas envoyer de data, just etablir une co, -w pour timeout)
```bash
nc -z -w 1 10.44.10.144 7854;
nc -z -w 1 10.44.10.144 1803;
nc -z -w 1 10.44.10.144 4576;
ssh neuill@10.44.10.144
```
Le serveur nous laisse nous connecter et on peut entrer le mdp.
Il ne reste plus qu'à ls pour trouver falg.txt et l'obtenir avec
```bash
cat flag.txt
```

(Publié le 24 Novembre 2025 sur le discord de l'évenement)