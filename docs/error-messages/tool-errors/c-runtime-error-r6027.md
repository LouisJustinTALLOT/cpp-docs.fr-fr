---
description: 'En savoir plus sur : erreur Runtime C R6027'
title: Erreur Runtime C R6027
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 0f69972495d45de96585e9008ce24d53958fd7c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237463"
---
# <a name="c-runtime-error-r6027"></a>Erreur Runtime C R6027

espace insuffisant pour l’initialisation de lowio

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

Cette erreur se produit lorsque la mémoire disponible est insuffisante pour initialiser la prise en charge des e/s de bas niveau dans le runtime C. Cette erreur se produit généralement au démarrage de l’application. Vérifiez que votre application et les pilotes et les dll qu’elle charge n’endommagent pas le tas au démarrage.
