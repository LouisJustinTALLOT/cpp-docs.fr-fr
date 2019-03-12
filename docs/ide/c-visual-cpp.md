---
title: '&lt;c&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <c>
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
ms.openlocfilehash: a5eb88be4cb5be8c4e970c285bad712093fdbb51
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742602"
---
# <a name="ltcgt-visual-c"></a>&lt;c&gt; (Visual C++)

La balise \<c> indique que le texte d’une description doit être marqué comme étant du code. Utilisez [\<code>](../ide/code-visual-cpp.md) pour indiquer plusieurs lignes comme étant du code.

## <a name="syntax"></a>Syntaxe

```
<c>text</c>
```

#### <a name="parameters"></a>Paramètres

*texte*<br/>
Texte que vous souhaitez indiquer comme étant du code.

## <a name="remarks"></a>Remarques

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

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

[Documentation XML](../ide/xml-documentation-visual-cpp.md)
