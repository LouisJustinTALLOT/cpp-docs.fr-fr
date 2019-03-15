---
title: '&lt;exception > (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: 327c1bc27f4ae71aa214e09f375f963dad5b33d7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825431"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

La balise \<exception> vous permet de spécifier quelles exceptions peuvent être levées. Cette balise est appliquée à une définition de méthode.

## <a name="syntax"></a>Syntaxe

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Paramètres

*member*<br/>
Référence à une exception qui est disponible à partir de l’environnement de compilation actuel. À l’aide des règles de recherche de nom, le compilateur vérifie que l’exception donnée existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

Mettez le nom entre guillemets simples ou doubles.

Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](see-visual-cpp.md).

*description*<br/>
Description.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

Le compilateur MSVC tentera de résoudre les références cref en une seule passe via les commentaires de documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue. Pour plus d’informations, consultez [\<seealso>](seealso-visual-cpp.md).

## <a name="example"></a>Exemple

```
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
