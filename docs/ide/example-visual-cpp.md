---
title: '&lt;example&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: b1511bb77b35b054d83a64c1a832843e62a8daa9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744009"
---
# <a name="ltexamplegt-visual-c"></a>&lt;example&gt; (Visual C++)

La balise \<example> vous permet de spécifier un exemple d’utilisation d’une méthode ou de tout autre membre de bibliothèque. En règle générale, cela implique également l’utilisation de la balise [\<code>](../ide/code-visual-cpp.md).

## <a name="syntax"></a>Syntaxe

```
<example>description</example>
```

#### <a name="parameters"></a>Paramètres

*description*<br/>
Description de l’exemple de code.

## <a name="remarks"></a>Remarques

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```
// xml_example_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_example_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>
   /// GetZero method
   /// </summary>
   /// <example> This sample shows how to call the GetZero method.
   /// <code>
   /// int main()
   /// {
   ///    return GetZero();
   /// }
   /// </code>
   /// </example>
   static int GetZero() {
      return 0;
   }
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](../ide/xml-documentation-visual-cpp.md)
