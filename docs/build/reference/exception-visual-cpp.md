---
description: 'En savoir plus sur &lt; : &gt; balise d’exception'
title: '&lt;> d’exception (commentaires de documentation C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: c75f2a4a10386664e23b5ba730e1827c6d74af71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192419"
---
# <a name="ltexceptiongt-tag"></a>&lt;&gt;balise d’exception

La \<exception> balise vous permet de spécifier les exceptions qui peuvent être levées. Cette balise est appliquée à une définition de méthode.

## <a name="syntax"></a>Syntaxe

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Paramètres

*membre*<br/>
Référence à une exception qui est disponible à partir de l’environnement de compilation actuel. À l’aide des règles de recherche de nom, le compilateur vérifie que l’exception donnée existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

Mettez le nom entre guillemets simples ou doubles.

Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](see-visual-cpp.md) .

*description*<br/>
Une description.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

Le compilateur MSVC tente de résoudre les références CREF en une seule passe via les commentaires de documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue. [\<seealso>](seealso-visual-cpp.md)Pour plus d’informations, consultez.

## <a name="example"></a>Exemple

```cpp
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
