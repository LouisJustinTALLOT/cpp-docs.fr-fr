---
title: Erreur de génération de projet PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384100"
---
# <a name="project-build-error-prj0024"></a>Erreur de génération de projet PRJ0024

> Chemin d’accès Unicode '*chemin d’accès*' n’a pas pu être traduit dans la page de code ANSI de l’utilisateur.

*chemin d’accès* est la version Unicode d’origine de la chaîne de chemin d’accès. Cette erreur peut se produire dans les cas où il existe un chemin d’accès Unicode qui ne peut pas être converti directement en ANSI pour la page de codes système actuel.

Cette erreur peut se produire si vous travaillez avec un projet qui a été développé sur un système à l’aide d’une page de codes qui n’est pas sur votre ordinateur.

La résolution de cette erreur consiste à mettre à jour le chemin d’accès à utiliser le texte ANSI ou pour installer la page de codes sur votre ordinateur et définissez-la comme la valeur par défaut du système.