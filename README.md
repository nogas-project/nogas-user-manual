# Nogas manuel d'utilisation
<div align="center">
    <p>Créer par Yves-Shaheem Shedid et Mathieu Gouveia Sousa</p>
  <img style="width: 300px; height: 200px;" src="https://hackmd.io/_uploads/B1NoHrLsJx.svg" />
</div>

## Introduction 
Bienvenue dans le manuel d'utilisation pour l'application IDO NOGAS ! Ce guide vous aidera à bien débuter et à tirer le meilleur parti de ses fonctionnalités.

> [!TIP]
L'application est deployé et accessible de n'importe où, cependant,  puisqu'il doit être en votre proximité, c'est votre responsabilité comme utilisateur d'entretenir et d'assurer que l'appareil avec les capteurs (Raspberry Pi) soit démarrer avec les logiciels correspondants.

## Installation
### Prérequis 
- Module IDO (Raspberry Pi)
- Une connexion Internet

### Étapes
Nogas est composé de 3 components séparé en trois repositoires. Le `README` de chaque repositoire contient les informations pour l'installation et le démarrage. La DB (Firestore) est hébergé par Google Firebase.
> [!Warning]
> Assurez-vous d'avoir les fichiers .env bien configuré. Si vous-souhaitez lancer le backend sur votre propre machine, vous aurez besoin d'un ficher JSON adminsdk afin d'interagir avec votre DB Firestore, ce fichier est générer dans la console Firebase.
1. Brancher le Module (le raspberry-pi)
2. Connecter le à Internet (brancher un clavier et souris)
3. Lire le `README` [IDO](https://github.com/Yves-Shaheem/NoGas_IDO)

### Optionnel
Ces components sont déja déployé, mais si vous-souhaitez les lancer sur votre propre machine.
1. Lire le `README` [FRONTEND](https://github.com/Yves-Shaheem/NoGas_FE)
2. Lire le `README` [BACKEND](https://github.com/Yves-Shaheem/NoGas_BE)
3. Créer un compte Firebase, puis une DB Firestore
4. Générer un fichier adminsdk qui permettra le backend d'accéder la DB, puis insérer le dans le root du backend avec son path dans le .env

## Accéder le deployement
Après avoir démarrer le component IDO.
1. Diriger vous sur le site [nogas.ddns.net](https://nogas.ddns.net)
2. Créer un compte.
3. Se connecter au compte.
4. Accéder aux informations des capteurs sur `/home`

## Fonctionnalité et utilisation

### IDO
> Le raspberry-pi utlise le capteur de gaz pour récuper le niveau de gas présent dans la pièce.
>
> Le raspberry-pi envoie l'information récolter à l'API.
>
> Si ce niveau est dangereux une alarme débutera et un email sera envoyé au contacts d'urgences de l'utilisateur connecté.
>
> Pour désactiver cette alarme, il faut actionner le boutton de désarmement.

### API 
API Swagger Docs disponible [ici](https://nogas.ddns.net/api/v1/api-docs/)

> [!Warning]
> - Certains requêtes sont seulement autorisé par un admin, ou par l'utilisateur dont les données lui appartient
> - Assurez-vous d'avoir correctement inséré le JWT sans les marques d'un String, sinon l'autorization ne fonctionnera PAS
```bash
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9eyJpZCI6MCwiYWRtaW4iOmZhbHNlLCJpYXQiOjE3NDA0MjM5MjYsImV4cCI6MTc0MDQ1MjcyNn0.Vu1m1UTbxdxYMFTjAxuBO8F-3thzjdxoUs4VtmZjjbg
PAS "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9eyJpZCI6MCwiYWRtaW4iOmZhbHNlLCJpYXQiOjE3NDA0MjM5MjYsImV4cCI6MTc0MDQ1MjcyNn0.Vu1m1UTbxdxYMFTjAxuBO8F-3thzjdxoUs4VtmZjjbg"
```

### Interface utilisateur
`/` 
> Landing page
>
> Route public 
>
> Sert à accueillir l'utilisateur 
>
> Utilisateur peut se créer un compte, se connecter et apprendre plus sur le site

`/register` 
> Page de création de compte.
>
> Route public 
>
> Sert à se créer un compte et redirige vers la page de connexion.
>
> Utlisateur peut remplir le formulaire ou sinon se connecter s'il a un compte déja.

`/login` 
> Page de connexion.
>
> Route public. 
>
> Sert à se connecter et redirige vers la page profile.
>
> Utilisateur peut se connecter ou sinon se créer un compte s'il en n'a pas.

`/about`
> Page d'information.
> 
> Route public.
> 
> Barre de navigation apparait si l'utilisateur est connecté. 
> 
> Sert à l'utlisateur de l'information concernant le projet. 

`/profile`
> Page de profile de l'utilisateur. 
> 
> Route privée.
> 
> Sert à modifier toute information sur son compte incluant ses contacts.
> 
> Utilisateur peut modifier son compte ou sinon se déconnecter. 

`/home`
> Page d'information sur le gas.
>
> Route privée.
> 
> Sert à afficher les informations sur le gas et l'historique. 

Barre de navigation
> 
> Apparait lorsqu'on se connecte. 
> 
> Sert à naviguer dans le site, se déconnecter et désactiver/activer les notifications.

## Cas d'usages
|![signup](https://github.com/user-attachments/assets/f623072f-44d2-40c6-a097-f003b6951530)|
|:--:|
| Créer un compte |

|![about](https://github.com/user-attachments/assets/7ec3b880-cd51-4be1-9d38-3ddd0604883b)|
|:--:|
| Accèder about page |

|![login](https://github.com/user-attachments/assets/f72e79ee-0e9c-4f92-8103-df539d4a2470)|
|:--:|
| Se connecter |

|![modify_profile](https://github.com/user-attachments/assets/ec38034b-1a79-44ad-81a8-6e2ad3439197)|
|:--:|
| Modifier son profile |

|![home](https://github.com/user-attachments/assets/7999f2ac-4763-4e50-96e1-4f9990b90438)|
|:--:|
| Accèder la page home |

|![logout](https://github.com/user-attachments/assets/95dfcc69-d1b4-4c8f-b60d-eecd856633d6)|
|:--:|
| Se déconnecter |

## FAQ
**Q: Je n'arrive pas à utiliser Swagger-docs**
A: Assurez-vous d'avoir [bien mis](API) le JWT dans l'autorization Swagger, et si le cas, que ce JWT sois admin ou provient de l'utilisateur dont les données vous-voulez accèder.

**Q: Pourquoi dois-je mettre un nouveau mot de passe chaque fois que je modifie mon profile?**
A: Afin de vérifier que vous-êtes le propriétaire du compte, le mot de passe est requis lors des changements de données, vous-pouvez remettre le même.

**Q: Comment peux-je créer un compte admin?**
A: Ce rôle est strictement utilisé pour l'envoi de courriel et de données provenant du capteur. Sa création n'est pas voulu, puisqu'un est déja créer et n'est pas utile hors du fonctionnement arrière de l'application.
