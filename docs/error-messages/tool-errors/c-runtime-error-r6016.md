---
description: 'En savoir plus sur : erreur Runtime C R6016'
title: Erreur Runtime C R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: 79339400436f21aefc0edea101b4642d443f5ce0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237684"
---
# <a name="c-runtime-error-r6016"></a>Erreur Runtime C R6016

espace insuffisant pour les données du thread

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Cette erreur peut avoir plusieurs causes, mais elle est souvent due à une condition de mémoire extrêmement faible, à un bogue dans l’application ou à un bogue dans un complément ou une extension utilisée par l’application.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller l’application.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour supprimer, réparer ou réinstaller les compléments ou extensions utilisés par l’application.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur se produit car le programme n’a pas reçu suffisamment de mémoire du système d’exploitation pour effectuer une [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) ou un `_beginthreadex` appel, ou le stockage local des threads n’a pas été initialisé par `_beginthread` ou `_beginthreadex` .

Quand un nouveau thread est lancé, la bibliothèque doit créer une base de données interne pour le thread. Si la base de données ne peut pas être développée à l’aide de la mémoire fournie par le système d’exploitation, le thread ne démarre pas et le processus d’appel s’arrête. Cela peut se produire lorsque de trop nombreux threads ont été créés par le processus, ou si le stockage local des threads est épuisé.

Nous vous recommandons d’utiliser un fichier exécutable qui appelle la bibliothèque Runtime C (CRT) `_beginthreadex` pour la création de threads plutôt que l’API Windows `CreateThread` . `_beginthreadex` initialise le stockage statique interne utilisé par de nombreuses fonctions CRT dans le stockage local des threads. Si vous utilisez `CreateThread` pour créer un thread, la bibliothèque Runtime C (CRT) peut terminer le processus avec R6016 lorsqu'un appel est effectué à destination d'une fonction CRT qui nécessite l'initialisation du stockage statique interne.
