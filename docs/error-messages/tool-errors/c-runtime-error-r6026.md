---
description: 'En savoir plus sur : erreur Runtime C R6026'
title: Erreur Runtime C R6026
ms.date: 11/04/2016
f1_keywords:
- R6026
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
ms.openlocfilehash: f592cfff4dab72cbaac3d6470fdb2423302a08c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237528"
---
# <a name="c-runtime-error-r6026"></a>Erreur Runtime C R6026

espace insuffisant pour l’initialisation stdio

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Il existe plusieurs raisons possibles pour cette erreur, mais elle est généralement due à une condition de mémoire extrêmement faible. Il peut également être provoqué par un bogue dans l’application, par l’altération des bibliothèques Visual C++ qu’il utilise ou par un pilote.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Si l’application fonctionnait avant une installation récente d’une autre application ou d’un pilote, utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** dans le **panneau de configuration** pour supprimer la nouvelle application ou le pilote, puis réessayez d’exécuter votre application.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller toutes les copies du Microsoft Visual C++ redistribuable.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur se produit lorsque la mémoire disponible est insuffisante pour initialiser la prise en charge des e/s standard dans le runtime C. Cette erreur se produit généralement au démarrage de l’application. Vérifiez que votre application et les pilotes et les dll qu’elle charge n’endommagent pas le tas au démarrage.
