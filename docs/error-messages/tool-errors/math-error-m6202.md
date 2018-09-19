---
title: Erreur mathématique M6202 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 328336e61c299cf9b9816ddfce7212f1798eae37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058547"
---
# <a name="math-error-m6202"></a>Erreur mathématique M6202

'fonction' : erreur

Un argument de la fonction était une valeur de singularité pour cette fonction. La fonction n’est pas définie pour cet argument.

Cette erreur appelle le `_matherr` fonction avec le nom de fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction permettant de personnaliser la gestion de certaines erreurs mathématiques à virgule flottante d’exécution.