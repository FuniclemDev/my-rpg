# Architecture

Tout l'état du jeu vit dans une structure `all_t` (`include/struct.h`) créée par `initialize_all()` :
fenêtre, état courant (menu, sauvegardes, en jeu, réglages, dialogue), personnage, liste chaînée d'ennemis,
inventaire, coffres, dialogues, décor.

## Boucle principale (`src/main.c`)

```
while (fenêtre ouverte)
    mouse_pos()      position souris ramenée à la résolution logique (720p ou 1080p)
    analyse_event()  événements clavier / souris selon l'état courant
    draw_screen()    menu, sauvegardes, jeu, ennemis, dialogue, réglages, aide
```

`./my_rpg -h` affiche l'aide ; le binaire se lance depuis la racine du dépôt (les chemins des assets sont relatifs).

## Dossiers de `src/`

| Dossier | Rôle |
| --- | --- |
| `create/` | création de la fenêtre, des boutons, du personnage et des chars, de l'herbe en tuiles, du décor (`creat_decor.c` lit `info/doc`) |
| `events/` | menu, jeu (déplacement `Z Q S D`, tir), dialogues (`event_dial.c`), ennemis (`event_ennemy.c` : poursuite, dégâts, Game Over) |
| `draws/` | dessin du menu, de la carte, du personnage, des chars |
| `button_manager/` | boutons du menu, des sauvegardes et des réglages, changement de résolution (`resize_all_sprites.c`) |
| `inventory/`, `coffre/`, `object/`, `arme/` | inventaire (`F`), coffres (`E`), glisser-déposer des objets, armes |
| `saves/` | trois emplacements `partyN.save` : position, équipement, ennemis encore en vie |
| `destroy/` | libération des ressources CSFML |

## Données

- `info/doc` : pour chaque sprite de décor, son rectangle dans l'image puis la liste de ses positions `x_y/`.
- `assets/collision/` : un masque par objet de décor ; les zones rouges bloquent le passage, testées pixel par pixel.
- `info/*.txt` : textes des dialogues du colonel.
