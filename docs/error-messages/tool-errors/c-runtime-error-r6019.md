---
title: Erreur Runtime C R6019 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95bc763ab39df16c1cfc1b05689560edecf70570
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093300"
---
# <a name="c-runtime-error-r6019"></a>Erreur Runtime C R6019

Impossible d’ouvrir le périphérique de la console

> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle a tenté d’accéder à la console, mais il n’avait pas une autorisation suffisante. Il existe plusieurs raisons possibles à cette erreur, mais il est généralement parce que le programme doit être exécuté en tant qu’administrateur, ou il existe un bogue dans le programme.
>
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
>  -   Exécutez le programme en tant qu’administrateur.
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.
> -   Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> -   Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Cette erreur se produit parce que l’application a appelé une fonction de la console, mais le système d’exploitation n’a pas accordé l’accès à la console. À l’exception en mode débogage, fonctions de la console sont généralement pas autorisées dans les applications Microsoft Store. Si votre application requiert des privilèges d’administrateur pour exécuter, vérifiez qu’il est installé pour s’exécuter en tant qu’administrateur par défaut.