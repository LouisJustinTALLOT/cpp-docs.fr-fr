---
description: En savoir plus sur l’accès aux arguments
title: Accès aux arguments
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: f62ac2bc4ae895afe763d0a0a4caa32601e82713
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221863"
---
# <a name="argument-access"></a>Accès aux arguments

Les macros **va_arg**, **va_end** et **va_start** fournissent l’accès aux arguments de fonction quand le nombre d’arguments est variable. Ces macros sont définies dans \<stdarg.h> pour la compatibilité ANSI/ISO C et dans \<varargs.h> pour la compatibilité avec UNIX System V.

## <a name="argument-access-macros"></a>Macros d’accès à un argument

|Macro|Utilisation|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Récupérer un argument dans la liste|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Réinitialiser le pointeur|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Définir le pointeur au début de la liste d’arguments|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
