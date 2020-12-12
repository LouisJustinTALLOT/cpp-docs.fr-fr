---
description: 'En savoir plus sur : erreur du compilateur C2813'
title: Erreur du compilateur C2813
ms.date: 11/04/2016
f1_keywords:
- C2813
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
ms.openlocfilehash: 51de4100da8c0dd1a3b2ad1857799769b2abea24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278400"
---
# <a name="compiler-error-c2813"></a>Erreur du compilateur C2813

\#l’importation n’est pas prise en charge avec/MP

L’erreur C2813 est émise si, dans une commande du compilateur, vous spécifiez l’option du compilateur **/MP** , deux fichiers ou plus à compiler et qu’un ou plusieurs des fichiers contiennent la directive de préprocesseur [#import](../../preprocessor/hash-import-directive-cpp.md) . La directive [#import](../../preprocessor/hash-import-directive-cpp.md) génère des classes C++ à partir des types dans la bibliothèque de types spécifiée, puis écrit ces classes dans deux fichiers d’en-tête. La directive [#import](../../preprocessor/hash-import-directive-cpp.md) n’est pas prise en charge, car si plusieurs unités de compilation importent la même bibliothèque de types, ces unités sont en conflit quand elles essaient d’écrire les mêmes fichiers d’en-tête en même temps.

Cette erreur du compilateur et l’option du compilateur **/MP** sont nouvelles dans Visual Studio 2008.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2813. La ligne de commande située dans le commentaire « compiler avec : » indique au compilateur d’utiliser les options **/MP** et **/c** pour compiler plusieurs fichiers. Au moins un des fichiers contient la directive [#import](../../preprocessor/hash-import-directive-cpp.md) . Nous utilisons le même fichier à deux reprises pour tester cet exemple.

```cpp
// C2813.cpp
// compile with: /MP /c C2813.cpp C2813.cpp
#import "C:\windows\system32\stdole2.tlb"   // C2813
int main()
{
}
```
