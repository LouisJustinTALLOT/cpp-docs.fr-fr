---
description: 'En savoir plus sur : &lt; c&gt;'
title: '&lt;c> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <c>
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
ms.openlocfilehash: 35d06183136a82c602b5e4daa288fb4518962154
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182617"
---
# <a name="ltcgt"></a>&lt;c&gt;

La \<c> balise indique que le texte d’une description doit être marqué comme étant du code. Utilisez [\<code>](code-visual-cpp.md) pour indiquer plusieurs lignes en tant que code.

## <a name="syntax"></a>Syntaxe

```
<c>text</c>
```

#### <a name="parameters"></a>Paramètres

*text*<br/>
Texte que vous souhaitez indiquer comme étant du code.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

## <a name="example"></a>Exemple

```cpp
// xml_c_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_c_tag.xdc

/// Text for class MyClass.
class MyClass {
public:
   int m_i;
   MyClass() : m_i(0) {}

   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.
   /// </summary>
   int MyMethod(MyClass * a) {
      return a -> m_i;
   }
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
