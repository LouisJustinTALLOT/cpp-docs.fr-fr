---
title: Erreur Runtime C R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: b36e2184e5be131645fb4dd58a361fdb9a31da63
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774971"
---
# <a name="c-runtime-error-r6018"></a>Erreur Runtime C R6018

Erreur de tas inattendue

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Il existe plusieurs raisons possibles à cette erreur, mais souvent, elle est provoquée par un défaut dans le code de l’application.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Le programme a rencontré une erreur inattendue lors d’une opération de gestion de la mémoire.

Cette erreur se produit généralement quand le programme modifie par inadvertance les données du tas de l’exécution. Cependant, il peut également être dû à une erreur interne dans le runtime ou le code de système d’exploitation.

Pour résoudre ce problème, recherchez les bogues d’altération du tas dans votre code. Pour plus d’informations et des exemples, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Ensuite, vérifiez que vous utilisez les derniers redistribuables pour votre déploiement d’application. Pour plus d’informations, consultez [déploiement dans Visual C++](../../windows/deployment-in-visual-cpp.md).