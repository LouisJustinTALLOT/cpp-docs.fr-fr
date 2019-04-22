---
title: Erreur Runtime C R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 45f3b07f540cb72a955b19420130a5a806b750d7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774696"
---
# <a name="c-runtime-error-r6017"></a>Erreur Runtime C R6017

Erreur de verrouillage multithread inattendue

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Il existe plusieurs raisons possibles à cette erreur, mais souvent, elle est provoquée par un défaut dans le code de l’application.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> - Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Le processus a reçu une erreur inattendue en essayant d’accéder à un verrou multithread du runtime C sur une ressource système. Cette erreur se produit généralement quand le processus modifie par inadvertance les données de segment de mémoire d’exécution. Cependant, il peut également être dû à une erreur interne dans la bibliothèque runtime ou le code du système d’exploitation.

Pour résoudre ce problème, recherchez les bogues d’altération du tas dans votre code. Pour plus d’informations et des exemples, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Ensuite, vérifiez que vous utilisez les derniers redistribuables pour votre déploiement d’application. Pour plus d’informations, consultez [déploiement dans Visual C++](../../windows/deployment-in-visual-cpp.md).