---
title: '&lt;param&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- param
- <param>
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
ms.openlocfilehash: ec570a1c8b66e12474a2d960ed1b4f4b5e21b219
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651332"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)

La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode.

## <a name="syntax"></a>Syntaxe

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>Paramètres

*name*<br/>
Nom d’un paramètre de méthode.  Mettez le nom entre guillemets simples ou doubles.  Le compilateur émet un avertissement s'il ne trouve pas `name`.

*description*<br/>
Description du paramètre.

## <a name="remarks"></a>Notes

Le texte de la balise \<param> s’affiche dans IntelliSense, dans [l’Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport web de commentaire de code.

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](../ide/xml-documentation-visual-cpp.md)