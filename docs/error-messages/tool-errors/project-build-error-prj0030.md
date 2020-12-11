---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0030'
title: Erreur de génération de projet PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: a8fdb99e7444383f3634730b3053b00b81661aed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160283"
---
# <a name="project-build-error-prj0030"></a>Erreur de génération de projet PRJ0030

Erreur d’expansion de macro. L’évaluation de la récurrence a dépassé 32 niveaux pour $ (macro).

Cette erreur est provoquée par la récursivité dans vos macros. Par exemple, si vous affectez la valeur $ (IntDir) à la propriété **Intermediate Directory** (consultez [général, page de propriétés (projet)](../../build/reference/general-property-page-project.md)), vous aurez la récursivité.

Pour résoudre cette erreur, ne définissez pas de macros ou de propriétés en termes de macros qu’elles sont utilisées pour définir.
