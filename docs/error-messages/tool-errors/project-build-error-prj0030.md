---
title: Erreur de génération de projet PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811474"
---
# <a name="project-build-error-prj0030"></a>Erreur de génération de projet PRJ0030

Erreur d’expansion macro. Récurrence d’évaluation a dépassé 32 niveaux pour $(macro).

Cette erreur est due à la récursivité dans vos macros. Par exemple, si vous définissez la **répertoire intermédiaire** propriété (consultez [General Property Page (Project)](../../build/reference/general-property-page-project.md)) $ (IntDir), vous aurez la récursivité.

Pour résoudre cette erreur, ne définissez pas les macros ou des propriétés en termes de macros, qu'ils servent à définir.