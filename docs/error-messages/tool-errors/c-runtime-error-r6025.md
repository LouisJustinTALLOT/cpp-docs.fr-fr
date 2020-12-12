---
description: 'En savoir plus sur : erreur Runtime C R6025'
title: Erreur Runtime C R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 7bf3213d81e144f14f6eeb25f108f497267ec4d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237567"
---
# <a name="c-runtime-error-r6025"></a>Erreur Runtime C R6025

appel de fonction virtuelle pure

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. La raison la plus courante de cette erreur est un bogue dans l’application ou une installation endommagée.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Aucun objet n’a été instancié pour gérer l’appel de fonction virtuelle pure.

Cette erreur est provoquée par l’appel d’une fonction virtuelle dans une classe de base abstraite par le biais d’un pointeur créé par un cast vers le type de la classe dérivée, mais qui est en fait un pointeur vers la classe de base. Cela peut se produire lors de la conversion d’un **`void`** <strong>\*</strong> en pointeur vers une classe lorsque le **`void`** <strong>\*</strong> a été créé pendant la construction de la classe de base.
