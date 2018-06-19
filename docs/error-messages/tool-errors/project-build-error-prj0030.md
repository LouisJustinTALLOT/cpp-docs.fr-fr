---
title: PRJ0030 d’erreur de Build de projet | Documents Microsoft
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
ms.openlocfilehash: 1bf1c9137f8c4ed0d80955eef38b07ea86204a5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317656"
---
# <a name="project-build-error-prj0030"></a>Erreur de génération de projet PRJ0030
Erreur d’expansion macro. Récurrence d’évaluation a dépassé 32 niveaux pour $(macro).  
  
 Cette erreur est due à la récursivité dans vos macros. Par exemple, si vous définissez la **répertoire intermédiaire** propriété (voir [général, Page de propriétés (projet)](../../ide/general-property-page-project.md)) $ (IntDir), vous devez la récursivité.  
  
 Pour résoudre cette erreur, ne définissez pas les propriétés en termes de macros que qui sont utilisées pour définir ou macros.