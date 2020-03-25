---
title: Erreur Runtime C R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197300"
---
# <a name="c-runtime-error-r6017"></a>Erreur Runtime C R6017

erreur de verrouillage multithread inattendue

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème interne. Il existe plusieurs raisons possibles pour cette erreur, mais elle est souvent due à un défaut dans le code de l’application.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Le processus a reçu une erreur inattendue lors de la tentative d’accès à un verrou multithread du runtime C sur une ressource système. Cette erreur se produit généralement si le processus modifie par inadvertance les données du tas du Runtime. Toutefois, cela peut également être dû à une erreur interne dans la bibliothèque d’exécution ou dans le code du système d’exploitation.

Pour résoudre ce problème, recherchez les bogues d’altération du tas dans votre code. Pour plus d’informations et d’exemples, consultez [Détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details). Ensuite, vérifiez que vous utilisez les fichiers redistribuables les plus récents pour le déploiement de votre application. Pour plus d’informations, consultez [déploiement C++dans Visual ](../../windows/deployment-in-visual-cpp.md).
