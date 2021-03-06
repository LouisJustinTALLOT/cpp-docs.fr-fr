---
description: 'En savoir plus sur : erreur Runtime C R6031'
title: Erreur Runtime C R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: cd3a9e62e4209df5aa232ac9df6b69ce8a63d10a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206615"
---
# <a name="c-runtime-error-r6031"></a>Erreur Runtime C R6031

Essayez d’initialiser le CRT plusieurs fois. Cela indique un bogue dans votre application.

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. Cela peut être dû à un bogue dans l’application, ou à un bogue dans un module complémentaire ou une extension que l’application utilise.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour supprimer, réparer ou réinstaller tous les programmes de complément ou d’extension utilisés par l’application.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Ce diagnostic indique que les instructions MSIL étaient en cours d’exécution pendant le verrouillage du chargeur. Pour plus d’informations, consultez [initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).
