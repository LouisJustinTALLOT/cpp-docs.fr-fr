---
title: Erreur Runtime C R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 60e6475a84d2662ad3718e04dba879dc06afeee7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214075"
---
# <a name="c-runtime-error-r6008"></a>Erreur Runtime C R6008

pas assez d’espace pour les arguments

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons possibles à cette erreur, mais il est souvent dû à une condition de mémoire très faibles, trop de mémoire effectuée par les variables d’environnement, ou d’un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> - Réduire le nombre et la taille des arguments de ligne de commande à l’application.
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Il a été suffisamment de mémoire pour charger le programme mais n’est pas suffisant pour créer le **argv** tableau. Cela peut résulter en conditions de mémoire ou en exceptionnellement élevé de lignes de commande ou l’utilisation de variables d’environnement. Envisagez l’une des solutions suivantes :

- Augmentez la quantité de mémoire disponible pour le programme.

- Réduire le nombre et la taille des arguments de ligne de commande.

- Réduire la taille de l’environnement en supprimant les variables superflues.