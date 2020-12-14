---
description: 'En savoir plus sur : erreur Runtime C R6018'
title: Erreur Runtime C R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: 778b57c7071ab6ce042c9e1c434541c1dbcfad13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237658"
---
# <a name="c-runtime-error-r6018"></a>Erreur Runtime C R6018

erreur de tas inattendue

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. Il existe plusieurs raisons possibles pour cette erreur, mais elle est souvent due à un défaut dans le code de l’application.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Le programme a rencontré une erreur inattendue lors de l’exécution d’une opération de gestion de la mémoire.

Cette erreur se produit généralement si le programme modifie par inadvertance les données du tas au moment de l’exécution. Toutefois, cela peut également être dû à une erreur interne dans le runtime ou dans le code du système d’exploitation.

Pour résoudre ce problème, recherchez les bogues d’altération du tas dans votre code. Pour plus d’informations et d’exemples, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details). Ensuite, vérifiez que vous utilisez les fichiers redistribuables les plus récents pour le déploiement de votre application. Pour plus d’informations, consultez [déploiement dans Visual C++](../../windows/deployment-in-visual-cpp.md).
