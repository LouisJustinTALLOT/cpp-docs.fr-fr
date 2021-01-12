---
description: 'En savoir plus sur : &lt; Voir&gt;'
title: '&lt;Voir> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: c1de0ec23854d159d661cd1b62df97169eab7317
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126219"
---
# <a name="ltseegt"></a>&lt;see&gt;

La \<see> balise vous permet de spécifier un lien à partir de texte. Utilisez [\<seealso>](seealso-visual-cpp.md) pour indiquer le texte que vous souhaitez voir apparaître dans une section Voir aussi.

## <a name="syntax"></a>Syntaxe

```
<see cref="member"/>
```

#### <a name="parameters"></a>Paramètres

*membre*<br/>
Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.  Mettez le nom entre guillemets simples ou doubles.

Le compilateur vérifie que l’élément de code donné existe et qu’il résout `member` en nom d’élément dans le code XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

[\<summary>](summary-visual-cpp.md)Pour obtenir un exemple d’utilisation de \<see> , consultez.

Le compilateur MSVC tente de résoudre les références CREF en une seule passe via les commentaires de documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue. [\<seealso>](seealso-visual-cpp.md)Pour plus d’informations, consultez.

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
