---
title: "Erreur LNK2022 des outils Éditeur de liens | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2022
dev_langs: C++
helpviewer_keywords: LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 022ad56460ad666a5d02c4f176093f16a82b4e40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2022"></a>Erreur des outils Éditeur de liens LNK2022  
  
> échoué de l’opération métadonnées (*HRESULT*) : *error_message*  
  
L’éditeur de liens a détecté une erreur lors de la fusion des métadonnées. Les erreurs de métadonnées doivent être résolues pour lier correctement.  
  
Une façon de diagnostiquer ce problème consiste à exécuter **ildasm-jetons** sur les fichiers objets pour rechercher les types dont les jetons sont répertoriés dans `error_message`et rechercher les différences.  Dans les métadonnées, deux types différents portant le même nom n’est pas valide, même si l’attribut LayoutType juste est différent.  
  
Une raison de LNK2022 est qu’un type (par exemple, une structure) existe dans plusieurs modules (compilands) avec le même nom mais avec des définitions, et lorsque vous compilez avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  Dans ce cas, assurez-vous que le type a une définition identique dans tous les modules (compilands).  Le nom du type est répertorié dans `error_message`.  
  
Erreur LNK2022 peut également se produire lorsque l’éditeur de liens détecte un fichier de métadonnées dans un emplacement différent de celui qui a été spécifié pour le compilateur (avec [#using](../../preprocessor/hash-using-directive-cpp.md) ). Assurez-vous que le fichier de métadonnées (.dll ou .netmodule) est dans le même emplacement que lorsqu’il est passé à l’éditeur de liens, telle qu’elle était lorsqu’elle a été passée au compilateur.  
  
Lors de la création d’une application ATL, l’utilisation de la macro `_ATL_MIXED` est requis dans tous les compilands, s’il est utilisé dans au moins un.  
  
## <a name="example"></a>Exemple  
  
L’exemple suivant définit un type vide.  
  
```cpp  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>Exemple  
  
Cet exemple montre que vous ne pouvez pas lier deux fichiers de code source qui contiennent des types portant le même nom mais des définitions différentes.  
  
L’exemple suivant génère l’erreur LNK2022.  
  
```cpp  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```