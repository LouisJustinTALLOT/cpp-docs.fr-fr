---
title: Erreur Runtime C R6028
ms.date: 11/04/2016
f1_keywords:
- R6028
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
ms.openlocfilehash: 4992641c2456f0322b5c52eb907b159904e4c9f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581816"
---
# <a name="c-runtime-error-r6028"></a>Erreur Runtime C R6028

impossible d'initialiser le tas

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons à cette erreur, mais souvent, elle est provoquée par une condition de mémoire extrêmement faible, un bogue dans le programme, ou par les pilotes de matériel défectueux.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Si l’application fonctionnait avant une installation récente d’une autre application ou de pilote, utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour supprimer le nouvelle application ou le pilote, puis réessayez votre application.
> - Consultez le site Web du fabricant de votre matériel ou **mise à jour Windows** dans le **le panneau de configuration** des mises à jour de pilote et du logiciel.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Cette erreur se produit lorsque le système d'exploitation ne parvient pas à créer le pool de mémoire pour l'application ; plus particulièrement, CRT (C Runtime) a appelé la fonction Win32 `HeapCreate`, qui a retourné la valeur NULL, ce qui indique un échec.

Si cette erreur se produit au démarrage de l'application, le système n'est peut-être pas en mesure de répondre aux requêtes de tas, en raison du chargement de pilotes défectueux. Consultez le site Web Windows Update ou le site Web du fabricant de votre matériel pour obtenir des pilotes mis à jour.