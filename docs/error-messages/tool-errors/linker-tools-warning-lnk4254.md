---
title: Avertissement des outils Éditeur de liens LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 2c68e49d58b0fd6b28607eb0ba78c092441f6f4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352487"
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