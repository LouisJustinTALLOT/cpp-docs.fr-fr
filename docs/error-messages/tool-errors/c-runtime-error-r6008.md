---
title: Erreur Runtime C R6008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b06566f84003b08f5fe3869a021c4bf86dcf5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105127"
---
# <a name="c-runtime-error-r6008"></a>Erreur Runtime C R6008

pas assez d’espace pour les arguments

> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons possibles à cette erreur, mais il est souvent dû à une condition de mémoire très faibles, trop de mémoire effectuée par les variables d’environnement, ou d’un bogue dans le programme.
>
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
>  -   Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> -   Réduire le nombre et la taille des arguments de ligne de commande à l’application.
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> -   Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> -   Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Il a été suffisamment de mémoire pour charger le programme mais n’est pas suffisant pour créer le **argv** tableau. Cela peut résulter en conditions de mémoire ou en exceptionnellement élevé de lignes de commande ou l’utilisation de variables d’environnement. Envisagez l’une des solutions suivantes :

- Augmentez la quantité de mémoire disponible pour le programme.

- Réduire le nombre et la taille des arguments de ligne de commande.

- Réduire la taille de l’environnement en supprimant les variables superflues.