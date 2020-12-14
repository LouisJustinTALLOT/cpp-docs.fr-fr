---
description: 'En savoir plus sur : erreur Runtime C R6008'
title: Erreur Runtime C R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: d74bd647a4a4d844bb0b9bf0fe2f2d53994dc9ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237772"
---
# <a name="c-runtime-error-r6008"></a>Erreur Runtime C R6008

espace insuffisant pour les arguments

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Il existe plusieurs raisons possibles pour cette erreur, mais elle est souvent due à une condition de mémoire extrêmement faible, à une trop grande quantité de mémoire utilisée par les variables d’environnement ou à un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Réduisez le nombre et la taille des arguments de ligne de commande à l’application.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

La mémoire est insuffisante pour charger le programme, mais la mémoire est insuffisante pour créer le tableau **argv** . Cela peut être dû à des conditions de mémoire extrêmement basses ou à des lignes de commande ou à une utilisation de variables d’environnement exceptionnellement élevées. Envisagez l’une des solutions suivantes :

- Augmentez la quantité de mémoire disponible pour le programme.

- Réduisez le nombre et la taille des arguments de ligne de commande.

- Réduisez la taille de l’environnement en supprimant les variables inutiles.
