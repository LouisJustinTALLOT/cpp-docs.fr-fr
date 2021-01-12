---
description: 'En savoir plus sur : &lt; exemple&gt;'
title: '&lt;exemple> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <example>
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: 61624efd34c02d75c7109a3211914b2018c513ae
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98125881"
---
# <a name="ltexamplegt"></a>&lt;example&gt;

La \<example> balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque. En général, cela implique également l’utilisation de la [\<code>](code-visual-cpp.md) balise.

## <a name="syntax"></a>Syntaxe

```
<example>description</example>
```

#### <a name="parameters"></a>Paramètres

*description*<br/>
Description de l’exemple de code.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

## <a name="example"></a>Exemple

```cpp
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

[Documentation XML](xml-documentation-visual-cpp.md)
