---
title: Avertissement des outils Éditeur de liens LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: d2fd7238a3f57b11b91813bd40b66cb3e9f47202
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352518"
---
# <a name="linker-tools-warning-lnk4253"></a>Avertissement des outils Éditeur de liens LNK4253

section 'section1' non fusionnée dans 'section2' ; déjà fusionnée dans 'section3'

L’éditeur de liens a détecté plusieurs demandes de fusion en conflit. L’éditeur de liens ignore l’une des demandes.

A **/fusion** option ou la directive est rencontrée et le `from` section a déjà été fusionnée dans une section différente en raison d’une précédente **/fusion** option ou directive (ou en raison d’une fusion implicite de l’éditeur de liens).

Pour résoudre LNK4253, supprimez une des demandes de fusion.

Lorsque vous ciblez x86 machines et des cibles Windows CE (ARM, MIPS, SH4 et Thumb) avec Visual C++, le. Section de la bibliothèque CRT est désormais en lecture seule. Si votre code dépend du comportement précédent (. CRT sont en lecture/écriture), vous pouvez voir un comportement inattendu.

Pour plus d'informations, consultez

- [/MERGE (Combiner des sections)](../../build/reference/merge-combine-sections.md)

- [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Exemple

Dans l’exemple suivant, l’éditeur de liens est invité à fusionner la `.rdata` section à deux reprises, mais dans différentes sections. L’exemple suivant génère l’erreur LNK4253.

```
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```