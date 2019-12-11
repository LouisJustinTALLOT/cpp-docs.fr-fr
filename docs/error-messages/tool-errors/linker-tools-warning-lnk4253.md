---
title: Avertissement des outils Éditeur de liens LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988087"
---
# <a name="linker-tools-warning-lnk4253"></a>Avertissement des outils Éditeur de liens LNK4253

la section’Section1 'n’a pas été fusionnée dans’section2 '; déjà fusionné dans’section3 '

L’éditeur de liens a détecté plusieurs demandes de fusion en conflit. L’éditeur de liens ignore l’une des requêtes.

Une option ou une directive **/Merge** est rencontrée et la section `from` a déjà été fusionnée dans une autre section en raison d’une option ou d’une directive **/Merge** précédente (ou en raison d’une fusion implicite de l’éditeur de liens).

Pour résoudre LNK4253, supprimez l’une des demandes de fusion.

Lorsque vous ciblez des ordinateurs x86 et des cibles de Windows CE (ARM, MIPS, SH4 et C++Thumb) avec Visual, le. La section CRT est maintenant en lecture seule. Si votre code dépend du comportement précédent (. Les sections CRT sont en lecture/écriture), vous pouvez constater un comportement inattendu.

Pour plus d'informations, consultez

- [/MERGE (Combiner des sections)](../../build/reference/merge-combine-sections.md)

- [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Exemple

Dans l’exemple suivant, l’éditeur de liens est chargé de fusionner la section `.rdata` à deux reprises, mais dans des sections différentes. L’exemple suivant génère l’LNK4253.

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
