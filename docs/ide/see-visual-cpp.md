---
title: '&lt;see&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: c8e797dff1495e9b4573ab4e0820d60b8027a293
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747590"
---
# <a name="ltseegt-visual-c"></a>&lt;see&gt; (Visual C++)

La balise \<see> vous permet de spécifier un lien à partir de l’intérieur du texte. Utilisez [\<seealso>](../ide/seealso-visual-cpp.md) pour désigner le texte que vous souhaitez voir apparaître dans une section Voir aussi.

## <a name="syntax"></a>Syntaxe

```
<see cref="member"/>
```

#### <a name="parameters"></a>Paramètres

*member*<br/>
Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.  Mettez le nom entre guillemets simples ou doubles.

Le compilateur vérifie que l’élément de code donné existe et qu’il résout `member` en nom d’élément dans le code XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

## <a name="remarks"></a>Remarques

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

Pour un exemple d’utilisation de \<see>, consultez [\<summary>](../ide/summary-visual-cpp.md).

Le compilateur Visual C++ tente de résoudre les références cref en une seule passe via les commentaires de la documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue. Pour plus d’informations, consultez [\<seealso>](../ide/seealso-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer une référence cref à un type générique pour que le compilateur puisse résoudre la référence.

```
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

[Documentation XML](../ide/xml-documentation-visual-cpp.md)
