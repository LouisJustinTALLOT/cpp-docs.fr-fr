---
title: Erreur Runtime C R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 39d8a20dacb0cdeb2a767529e9716bd476f406dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400004"
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