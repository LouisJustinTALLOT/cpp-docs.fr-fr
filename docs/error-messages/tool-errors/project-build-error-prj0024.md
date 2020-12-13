---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0024'
title: Erreur de génération de projet PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: e42df62181d02cf8d4696cc4f48afcec52cd4d76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150460"
---
# <a name="project-build-error-prj0024"></a>Erreur de génération de projet PRJ0024

> Le chemin d’accès Unicode'*path*'n’a pas pu être traduit dans la page de codes ANSI de l’utilisateur.

*path* est la version Unicode d’origine de la chaîne de chemin d’accès. Cette erreur peut se produire dans les cas où il existe un chemin d’accès Unicode qui ne peut pas être traduit directement en ANSI pour la page de codes système actuelle.

Cette erreur peut se produire si vous travaillez avec un projet qui a été développé sur un système à l’aide d’une page de codes qui ne se trouve pas sur votre ordinateur.

La résolution de cette erreur consiste à mettre à jour le chemin d’accès pour utiliser du texte ANSI ou pour installer la page de codes sur votre ordinateur et la définir comme valeur système par défaut.
