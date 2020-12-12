---
description: 'En savoir plus sur : erreur Runtime C R6019'
title: Erreur Runtime C R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: 190b836d5c0823b3644e4ff49812b5de05f421e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237632"
---
# <a name="c-runtime-error-r6019"></a>Erreur Runtime C R6019

Impossible d’ouvrir l’appareil de la console

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle a tenté d’accéder à la console, mais elle ne dispose pas des autorisations suffisantes. Il existe plusieurs raisons possibles pour cette erreur, mais cela est généralement dû au fait que le programme doit être exécuté en tant qu’administrateur ou qu’il existe un bogue dans le programme.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Exécutez le programme en tant qu’administrateur.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur se produit parce que l’application a appelé une fonction de console, mais que le système d’exploitation n’a pas accordé l’accès à la console. Sauf en mode débogage, les fonctions de console ne sont généralement pas autorisées dans les applications Microsoft Store. Si votre application requiert des privilèges d’administrateur pour s’exécuter, assurez-vous qu’elle est installée pour s’exécuter en tant qu’administrateur par défaut.
