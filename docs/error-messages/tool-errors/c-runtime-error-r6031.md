---
title: Erreur Runtime C R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 6ef3f5fa7d063fdc300e6ac28ca519992525851c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564227"
---
# <a name="c-runtime-error-r6031"></a>Erreur Runtime C R6031

Tentative d’initialisation de la bibliothèque CRT plusieurs fois. Cela indique un bogue dans votre application.

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Cela peut être dû bogue dans l’application ou par un bogue dans un module complémentaire ou une extension qui utilise l’application.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour supprimer, réparer ou réinstaller tous les programmes complémentaires ou extension utilisées par l’application.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Ce diagnostic indique que des instructions MSIL sont exécutaient pendant le verrouillage du chargeur. Pour plus d’informations, consultez [l’initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).