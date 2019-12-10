---
title: '&lt;> paramref (C++ commentaires de documentation)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 1f4e9cb0e6b39e4da78e78048342dac2ecc9deea
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988693"
---
# <a name="ltparamrefgt"></a>&lt;paramref&gt;

La balise \<paramref> vous fournit un moyen d’indiquer qu’un mot est un paramètre. Le fichier .xml peut être traité pour mettre en forme ce paramètre de façon distincte.

## <a name="syntax"></a>Syntaxe

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Parameters

*name*<br/>
Nom du paramètre auquel faire référence.  Mettez le nom entre guillemets simples ou doubles.  Le compilateur émet un avertissement s'il ne trouve pas `name`.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```cpp
// xml_paramref_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_paramref_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <summary>MyMethod is a method in the MyClass class.
   /// The <paramref name="Int1"/> parameter takes a number.
   /// </summary>
   void MyMethod(int Int1) {}
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
