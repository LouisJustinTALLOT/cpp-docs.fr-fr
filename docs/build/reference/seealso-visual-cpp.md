---
title: '&lt;> seealso (C++ commentaires de documentation)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 698db2df462f561acd897d0d0e56b3106a915466
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988603"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi. Utilisez [\<see>](see-visual-cpp.md) pour spécifier un lien à partir de l’intérieur du texte.

## <a name="syntax"></a>Syntaxe

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parameters

*member*<br/>
Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.  Mettez le nom entre guillemets simples ou doubles.

Le compilateur vérifie que l’élément de code donné existe et qu’il résout `member` en nom d’élément dans le code XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](see-visual-cpp.md).

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

Pour obtenir un exemple d’utilisation de \<seealso>, consultez [\<summary>](summary-visual-cpp.md).

Le compilateur MSVC tente de résoudre les références CREF en une seule passe via les commentaires de documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue.

## <a name="example"></a>Exemple

Dans l’exemple suivant, un symbole non résolu est référencé dans un élément cref. Le commentaire XML pour la référence cref à B::Test est `<seealso cref="!:B::Test" />`, alors que la référence à A::Test est le code `<seealso cref="M:A.Test" />` bien formé.

```cpp
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
