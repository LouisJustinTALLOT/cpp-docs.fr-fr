---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4254'
title: Avertissement des outils Éditeur de liens LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 410a904af6af2015a817ac9e254dff7f09811b72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244470"
---
# <a name="linker-tools-warning-lnk4254"></a>Avertissement des outils Éditeur de liens LNK4254

section’Section1 ' (offset) fusionnée dans’section2 ' (offset) avec des attributs différents

Le contenu d’une section a été fusionné dans un autre, mais les attributs des deux sections sont différents. Votre programme peut fournir des résultats inattendus. Par exemple, les données que vous vouliez lire uniquement peuvent maintenant se trouver dans une section accessible en écriture.

Pour résoudre LNK4254, modifiez ou supprimez la demande de fusion.

Lorsque vous ciblez des ordinateurs x86 et des cibles de Windows CE (ARM, MIPS, SH4 et Thumb) avec Visual C++, le. La section CRT est en lecture seule. Si votre code dépend du comportement précédent (. Les sections CRT sont en lecture/écriture), vous pouvez constater un comportement inattendu.

Pour plus d'informations, consultez

- [/MERGE (combiner des sections)](../../build/reference/merge-combine-sections.md)

- [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK4254.

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
