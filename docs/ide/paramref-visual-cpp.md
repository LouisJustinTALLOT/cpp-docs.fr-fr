---
title: '&lt;paramref&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 7c1b8a79761e10209e26e1dee8a8751746c2f38c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744655"
---
# <a name="ltparamrefgt-visual-c"></a>&lt;paramref&gt; (Visual C++)

La balise \<paramref> vous fournit un moyen d’indiquer qu’un mot est un paramètre. Le fichier .xml peut être traité pour mettre en forme ce paramètre de façon distincte.

## <a name="syntax"></a>Syntaxe

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
Nom du paramètre auquel faire référence.  Mettez le nom entre guillemets simples ou doubles.  Le compilateur émet un avertissement s'il ne trouve pas `name`.

## <a name="remarks"></a>Remarques

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```
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

[Documentation XML](../ide/xml-documentation-visual-cpp.md)
