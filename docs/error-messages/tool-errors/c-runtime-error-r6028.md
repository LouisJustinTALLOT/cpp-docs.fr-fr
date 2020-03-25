---
title: Erreur Runtime C R6028
ms.date: 11/04/2016
f1_keywords:
- R6028
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
ms.openlocfilehash: 1c165b7c9351e34ef6316962cd90663f2b6152ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197130"
---
# <a name="c-runtime-error-r6028"></a>Erreur Runtime C R6028

impossible d'initialiser le tas

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Cette erreur peut avoir plusieurs causes, mais elle est souvent due à une condition de mémoire extrêmement faible, à un bogue dans le programme ou à des pilotes matériels défectueux.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Si l’application fonctionnait avant une installation récente d’une autre application ou d’un pilote, utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** dans le **panneau de configuration** pour supprimer la nouvelle application ou le pilote, puis réessayez d’exécuter votre application.
> - Consultez le site Web de votre fournisseur de matériel ou **Windows Update** dans le **panneau de configuration** pour les mises à jour des logiciels et des pilotes.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur se produit lorsque le système d'exploitation ne parvient pas à créer le pool de mémoire pour l'application ; plus particulièrement, CRT (C Runtime) a appelé la fonction Win32 `HeapCreate`, qui a retourné la valeur NULL, ce qui indique un échec.

Si cette erreur se produit au démarrage de l'application, le système n'est peut-être pas en mesure de répondre aux requêtes de tas, en raison du chargement de pilotes défectueux. Consultez le site web Windows Update ou le site web du fabricant de votre matériel pour obtenir des pilotes mis à jour.
