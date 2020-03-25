---
title: Erreur de génération de projet PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: bcfdcce54618acca0e22daa54e95083cf3ee9d50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192612"
---
# <a name="project-build-error-prj0024"></a>Erreur de génération de projet PRJ0024

> Le chemin d’accès Unicode'*path*'n’a pas pu être traduit dans la page de codes ANSI de l’utilisateur.

*path* est la version Unicode d’origine de la chaîne de chemin d’accès. Cette erreur peut se produire dans les cas où il existe un chemin d’accès Unicode qui ne peut pas être traduit directement en ANSI pour la page de codes système actuelle.

Cette erreur peut se produire si vous travaillez avec un projet qui a été développé sur un système à l’aide d’une page de codes qui ne se trouve pas sur votre ordinateur.

La résolution de cette erreur consiste à mettre à jour le chemin d’accès pour utiliser du texte ANSI ou pour installer la page de codes sur votre ordinateur et la définir comme valeur système par défaut.
