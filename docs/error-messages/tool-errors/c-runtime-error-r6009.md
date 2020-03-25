---
title: Erreur Runtime C R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 64391f8ec05a99bb85a9d6cd00d6488a945fdb62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197351"
---
# <a name="c-runtime-error-r6009"></a>Erreur Runtime C R6009

espace insuffisant pour l’environnement

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Il existe plusieurs raisons possibles pour cette erreur, mais elle est souvent due à une condition de mémoire extrêmement faible, à une trop grande quantité de mémoire utilisée par les variables d’environnement ou à un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

La mémoire est insuffisante pour charger le programme, mais la mémoire est insuffisante pour créer le tableau **envp** .  Cela peut être dû à des conditions de mémoire extrêmement insuffisantes ou à une utilisation inhabituelle de variables d’environnement. Envisagez l’une des solutions suivantes :

- Augmentez la quantité de mémoire disponible pour le programme.

- Réduisez le nombre et la taille des arguments de ligne de commande.

- Réduisez la taille de l’environnement en supprimant les variables inutiles.
