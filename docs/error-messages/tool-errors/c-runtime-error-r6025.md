---
title: Erreur Runtime C R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 461bfb2aa46053ec56fff67de70038b1fcd97389
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639560"
---
# <a name="c-runtime-error-r6025"></a>Erreur Runtime C R6025

appel de fonction virtuelle pure

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. La raison la plus courante de cette erreur est un bogue dans l’application ou une installation endommagée.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Aucun objet n’a été instancié pour gérer l’appel de fonction virtuelle pure.

Cette erreur est due en appelant une fonction virtuelle dans une classe de base abstraite via un pointeur qui est créé par un cast vers le type de la classe dérivée, mais est en fait un pointeur vers la classe de base. Cela peut se produire lors de la conversion à partir d’un **void** <strong>\*</strong> vers un pointeur vers une classe lors de la **void** <strong>\*</strong> a été créé pendant la construction de la classe de base.

