---
title: Erreur Runtime C R6016 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f4b4529e0faf433ff9dc5c4fc2c0594a4d9ff6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076643"
---
# <a name="c-runtime-error-r6016"></a>Erreur Runtime C R6016

espace insuffisant pour les données du thread

> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons à cette erreur, mais souvent, elle est provoquée par une condition de mémoire extrêmement faible, un bogue dans l’application, ou par un bogue dans un complément ou une extension utilisée par l’application.
>
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
>  -   Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller l’application.
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** à supprimer, réparer ou réinstaller les compléments ou les extensions utilisées par l’application.
> -   Vérifiez **mise à jour Windows** dans le **le panneau de configuration** mises à jour logicielles.
> -   Recherchez une version mise à jour de l’application. Contactez le fournisseur de l’application si le problème persiste.

**Informations pour les programmeurs**

Cette erreur se produit parce que le programme n’a pas reçu suffisamment de mémoire du système d’exploitation pour terminer un [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) ou `_beginthreadex` appel, ou thread stockage local n’a pas été initialisé par `_beginthread` ou `_beginthreadex`.

Quand un nouveau thread est lancé, la bibliothèque doit créer une base de données interne pour le thread. Si la base de données ne peut pas être étendue à l'aide de la mémoire fournie par le système d'exploitation, le thread ne démarre pas et le processus d'appel s'arrête. Cela peut se produire lorsque de trop nombreux threads ont été créés par le processus, ou si le stockage local des threads est épuisé.

Nous recommandons d’un exécutable qui appelle la bibliothèque de runtime C (CRT) doit utiliser `_beginthreadex` pour la création de threads plutôt que l’API Windows `CreateThread`. `_beginthreadex` initialise le stockage statique interne utilisé par de nombreuses fonctions CRT dans le stockage local des threads. Si vous utilisez `CreateThread` pour créer un thread, la bibliothèque Runtime C (CRT) peut terminer le processus avec R6016 lorsqu'un appel est effectué à destination d'une fonction CRT qui nécessite l'initialisation du stockage statique interne.