---
title: Erreur de génération PRJ0030 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964fedd40f577a8b337c4ad0c20ba80d33ed2a23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099901"
---
# <a name="project-build-error-prj0030"></a>Erreur de génération de projet PRJ0030

Erreur d’expansion macro. Récurrence d’évaluation a dépassé 32 niveaux pour $(macro).

Cette erreur est due à la récursivité dans vos macros. Par exemple, si vous définissez la **répertoire intermédiaire** propriété (consultez [General Property Page (Project)](../../ide/general-property-page-project.md)) $ (IntDir), vous aurez la récursivité.

Pour résoudre cette erreur, ne définissez pas les macros ou des propriétés en termes de macros, qu'ils servent à définir.