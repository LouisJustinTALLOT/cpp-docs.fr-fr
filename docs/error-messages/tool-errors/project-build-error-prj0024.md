---
title: Erreur de génération PRJ0024 de projet | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb539a5f1ee5f1aa5f9d828d93fa6d0dc8690c22
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215596"
---
# <a name="project-build-error-prj0024"></a>Erreur de génération de projet PRJ0024

> Chemin d’accès Unicode '*chemin d’accès*' n’a pas pu être traduit dans la page de code ANSI de l’utilisateur.

*chemin d’accès* est la version Unicode d’origine de la chaîne de chemin d’accès. Cette erreur peut se produire dans les cas où il existe un chemin d’accès Unicode qui ne peut pas être converti directement en ANSI pour la page de codes système actuel.

Cette erreur peut se produire si vous travaillez avec un projet qui a été développé sur un système à l’aide d’une page de codes qui n’est pas sur votre ordinateur.

La résolution de cette erreur consiste à mettre à jour le chemin d’accès à utiliser le texte ANSI ou pour installer la page de codes sur votre ordinateur et définissez-la comme la valeur par défaut du système.