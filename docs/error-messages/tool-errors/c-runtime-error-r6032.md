---
title: Erreur Runtime C R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: e0ae3acc491658840d74e262f3ab2719e613d60e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571338"
---
# <a name="c-runtime-error-r6032"></a>Erreur Runtime C R6032

Pas assez d’espace pour les informations de paramètres régionaux

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons possibles à cette erreur, mais souvent, elle est provoquée par une condition de mémoire, ou par un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Le runtime gère les informations sur les paramètres régionaux sur chaque thread afin qu’il puisse traiter les appels aux fonctions sensibles aux paramètres régionaux. Si l’allocation de la mémoire pour ces informations échoue, le runtime ne peut pas poursuivre car un trop grand nombre de ses services de base en dépendent.