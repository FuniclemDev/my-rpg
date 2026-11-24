# Installer et lancer le jeu sur Fedora

Testé sur Fedora 39.

```sh
sudo dnf install gcc make CSFML-devel
git clone git@github.com:FuniclemDev/my-rpg-source.git
cd my-rpg-source
make
./my_rpg
```

- Lancer `./my_rpg` **depuis la racine du dépôt** : les images, polices, sons et textes sont chargés en chemin relatif.
- `./my_rpg -h` affiche l'aide.
- La fenêtre s'ouvre en 1920×1080. Sur un écran plus petit, passer en 1280×720 avec la roue crantée du menu.
- Commandes : `Z` `Q` `S` `D` (AZERTY), `E` parler / ouvrir un coffre, `F` inventaire, clic gauche pour tirer.
- `make clean` / `make fclean` nettoient le dépôt.
