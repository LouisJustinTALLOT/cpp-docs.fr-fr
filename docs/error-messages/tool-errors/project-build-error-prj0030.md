---
title: Erreur de génération de projet PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 2a6cde4ca48acb9aadfe3109084483dbb554e1e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488073"
---
# <a name="project-build-error-prj0030"></a>Erreur de génération de projet PRJ0030

Erreur d’expansion macro. Récurrence d’évaluation a dépassé 32 niveaux pour $(macro).

Cette erreur est due à la récursivité dans vos macros. Par exemple, si vous définissez la **répertoire intermédiaire** propriété (consultez [General Property Page (Project)](../../ide/general-property-page-project.md)) $ (IntDir), vous aurez la récursivité.

Pour résoudre cette erreur, ne définissez pas les macros ou des propriétés en termes de macros, qu'ils servent à définir.