---
title: Erreur Runtime C R6033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64ff3069064b981ca1f4dd7b5c2d9a792cac8f26
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861876"
---
# <a name="c-runtime-error-r6033"></a>Erreur Runtime C R6033

Essayez d’utiliser le code MSIL de cet assembly pendant l’initialisation du code natif. Cela indique un bogue dans votre application. Il est très probablement le résultat de l’appel d’un code MSIL compilé (/ clr) à partir d’un constructeur natif ou de DllMain (fonction).

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Cette erreur peut être provoquée par un bogue dans l’application ou par un bogue dans un complément ou une extension qu’il utilise.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** à supprimer, réparer ou réinstaller des extensions ou des compléments.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Ce diagnostic indique que des instructions MSIL sont exécutaient pendant le verrouillage du chargeur. Cela peut se produire si vous avez compilé le code C++ natif à l’aide de l’indicateur/CLR. Utilisez uniquement l’indicateur/CLR sur les modules qui contiennent du code managé. Pour plus d’informations, consultez [l’initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).