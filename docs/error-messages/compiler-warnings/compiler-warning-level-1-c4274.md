---
title: Compilateur Warning (level 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: f73fa8e09baab127e7755ebe3def69c2fb585744
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028458"
---
# <a name="compiler-warning-level-1-c4274"></a>Compilateur Warning (level 1) C4274

\#ident ignored; see documentation for #pragma comment(exestr, 'string')

La `#ident` directive, qui insère une chaîne spécifiée par l’utilisateur dans l’objet ou le fichier exécutable, est déconseillée. Par conséquent, le compilateur ignore la directive.

> [!CAUTION]
>  Avertissement C4274 vous conseille d’utiliser le [#pragma comment (exestr, 'string')](../../preprocessor/comment-c-cpp.md) directive. Toutefois, ce Conseil est déconseillé et sera modifié dans une prochaine version du compilateur. Si vous utilisez le `#pragma` directive, l’outil de l’éditeur de liens (LINK.exe) ignore l’enregistrement de commentaires produit par la directive et émet un avertissement [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Au lieu du `#ident` directive, nous vous recommandons d’utiliser une chaîne de ressource de version de fichier dans votre application.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimer le `#ident "` *chaîne* `"` directive.

## <a name="see-also"></a>Voir aussi

[commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Avertissement des outils Éditeur de liens LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md)