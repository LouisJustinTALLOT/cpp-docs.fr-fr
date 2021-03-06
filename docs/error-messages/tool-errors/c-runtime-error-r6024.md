---
description: 'En savoir plus sur : erreur Runtime C R6024'
title: Erreur Runtime C R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: 165592e87eb38ab68c2435cc0a8ca53eb3bc16ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237593"
---
# <a name="c-runtime-error-r6024"></a>Erreur Runtime C R6024

espace insuffisant pour _onexit table/atexit

> [!NOTE]
> Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car elle présente un problème de mémoire interne. Cette erreur est généralement causée par une condition de mémoire extrêmement faible, ou rarement, par un bogue dans le programme ou par l’endommagement des bibliothèques Visual C++es qu’elle utilise.
>
> Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :
>
> - Fermez les autres applications en cours d’exécution ou redémarrez votre ordinateur pour libérer de la mémoire.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller le programme.
> - Utilisez la page **applications et fonctionnalités** ou **programmes et fonctionnalités** du **panneau de configuration** pour réparer ou réinstaller toutes les copies du Microsoft Visual C++ redistribuable.
> - Cochez **Windows Update** dans le **panneau de configuration** pour les mises à jour logicielles.
> - Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.

**Informations pour les programmeurs**

Cette erreur se produit parce qu’il n’y avait pas de mémoire disponible pour la `_onexit` `atexit` fonction ou. Cette erreur est due à une condition de mémoire insuffisante. Vous pouvez envisager de préallouer des tampons au démarrage de l’application pour faciliter l’enregistrement des données utilisateur et effectuer une sortie d’application propre dans des conditions de mémoire insuffisante.
