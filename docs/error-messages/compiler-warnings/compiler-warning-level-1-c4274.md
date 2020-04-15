---
title: Avertissement compilateur (niveau 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377077"
---
# <a name="compiler-warning-level-1-c4274"></a>Avertissement compilateur (niveau 1) C4274

\#ident ignoré; voir la documentation pour #pragma commentaire (exestr, 'string')

La `#ident` directive, qui insère une chaîne spécifiée par l’utilisateur dans l’objet ou le fichier exécutable, est dépréciée. Par conséquent, le compilateur ignore la directive.

> [!CAUTION]
> Avertissement C4274 vous conseille d’utiliser la [directive #pragma commentaire (exestr, «corde»).](../../preprocessor/comment-c-cpp.md) Toutefois, ce conseil est déprécié et sera révisé dans une version future du compilateur. Si vous `#pragma` utilisez la directive, l’outil de liaison (LINK.exe) ne tient pas compte de l’enregistrement de commentaires produit par la directive et émet l’avertissement [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Au lieu `#ident` de la directive, nous vous recommandons d’utiliser une chaîne de ressources de version de fichier dans votre application.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimer `#ident "`la directive *sur les cordes.* `"`

## <a name="see-also"></a>Voir aussi

[commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Linker Tools Avertissement LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md)
