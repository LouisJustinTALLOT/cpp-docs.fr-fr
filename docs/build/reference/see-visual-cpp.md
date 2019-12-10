---
title: '&lt;Voir > (C++ commentaires de documentation)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: 8693646fa37648d1b20c791d99d159f2c81b8ec1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988621"
---
# <a name="ltseegt"></a>&lt;see&gt;

La balise \<see> vous permet de spécifier un lien à partir de l’intérieur du texte. Utilisez [\<seealso>](seealso-visual-cpp.md) pour désigner le texte que vous souhaitez voir apparaître dans une section Voir aussi.

## <a name="syntax"></a>Syntaxe

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parameters

*member*<br/>
Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.  Mettez le nom entre guillemets simples ou doubles.

Le compilateur vérifie que l’élément de code donné existe et qu’il résout `member` en nom d’élément dans le code XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

Pour un exemple d’utilisation de \<see>, consultez [\<summary>](summary-visual-cpp.md).

Le compilateur MSVC tente de résoudre les références CREF en une seule passe via les commentaires de documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue. Pour plus d’informations, consultez [\<seealso>](seealso-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer une référence cref à un type générique pour que le compilateur puisse résoudre la référence.

```cpp
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
