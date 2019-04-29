---
title: Erreur Runtime C R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 5e1914d5d2f665609cfc24c2db3dc8a123d7e83f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299749"
---
# <a name="c-runtime-error-r6009"></a>Erreur Runtime C R6009

espace insuffisant pour l’environnement

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons possibles à cette erreur, mais il est souvent dû à une condition de mémoire très faibles, trop de mémoire effectuée par les variables d’environnement, ou d’un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Il a été suffisamment de mémoire pour charger le programme, mais pas assez de mémoire pour créer le **envp** tableau.  Cela peut résulter en conditions de mémoire ou en utilisation variable d’environnement exceptionnellement élevé. Envisagez l’une des solutions suivantes :

- Augmentez la quantité de mémoire disponible pour le programme.

- Réduire le nombre et la taille des arguments de ligne de commande.

- Réduire la taille de l’environnement en supprimant les variables superflues.