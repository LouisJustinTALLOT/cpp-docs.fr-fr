---
title: Avertissement LNK4254 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2ef421cbfa87ecab8a27dfa796eaa4eaacf7b70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064644"
---
# <a name="linker-tools-warning-lnk4254"></a>Avertissement des outils Éditeur de liens LNK4254

section 'section1' (offset) fusionnée dans 'section2' (offset) avec des attributs différents

Le contenu d’une section ont été fusionné dans un autre, mais les attributs des deux sections sont différents. Votre programme peut donner des résultats inattendus. Par exemple, vous souhaitez lire des données uniquement peuvent maintenant être dans une section accessible en écriture.

Pour résoudre l’erreur LNK4254, modifiez ou supprimez de la demande de fusion.

Lorsque vous ciblez x86 machines et des cibles Windows CE (ARM, MIPS, SH4 et Thumb) avec Visual C++, le. Section de la bibliothèque CRT est en lecture seule. Si votre code dépend du comportement précédent (. CRT sont en lecture/écriture), vous pouvez voir un comportement inattendu.

Pour plus d'informations, consultez

- [/MERGE (Combiner des sections)](../../build/reference/merge-combine-sections.md)

- [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK4254.

```
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```