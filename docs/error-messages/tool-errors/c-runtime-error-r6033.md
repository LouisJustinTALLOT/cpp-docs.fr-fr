---
title: Erreur Runtime C R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 86ac98a2635975b811c7b50020e4d4782675ae4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197015"
---
# <a name="c-runtime-error-r6033"></a>Erreur Runtime C R6033

Tentative d’utilisation du code MSIL de cet assembly pendant l’initialisation du code natif. Cela indique un bogue dans votre application. Il est très probable que le résultat de l’appel d’une fonction MSIL (/CLR) compilée à partir d’un constructeur natif ou de DllMain.

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. Cette erreur peut être causée par un bogue dans l’application, ou par un bogue dans un complément ou une extension qu’elle utilise.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour supprimer, réparer ou réinstaller des extensions ou des compléments.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Ce diagnostic indique que les instructions MSIL étaient en cours d’exécution pendant le verrouillage du chargeur. Cela peut se produire si vous avez compilé C++ en natif à l’aide de l’indicateur/CLR. Utilisez uniquement l’indicateur/CLR sur les modules qui contiennent du code managé. Pour plus d’informations, consultez [initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).
