---
title: Erreur mathématique M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173658"
---
# <a name="math-error-m6202"></a>Erreur mathématique M6202

'fonction' : erreur _SING

Un argument de la fonction donnée était une valeur de singularité pour cette fonction. La fonction n’est pas définie pour cet argument.

Cette erreur appelle la fonction `_matherr` avec le nom de la fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la fonction `_matherr` pour personnaliser la gestion de certaines erreurs mathématiques à virgule flottante au moment de l’exécution.
