---
description: 'En savoir plus sur : &lt; seealso&gt;'
title: '&lt;seealso> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 0d976d2f7e08690d1fc0209eaf399f2368930327
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126193"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

La \<seealso> balise vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi. Utilisez [\<see>](see-visual-cpp.md) pour spécifier un lien à partir de texte.

## <a name="syntax"></a>Syntaxe

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Paramètres

*membre*<br/>
Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.  Mettez le nom entre guillemets simples ou doubles.

Le compilateur vérifie que l’élément de code donné existe et qu’il résout `member` en nom d’élément dans le code XML de sortie.  Le compilateur émet un avertissement s'il ne trouve pas `member`.

Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](see-visual-cpp.md) .

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

[\<summary>](summary-visual-cpp.md)Pour obtenir un exemple d’utilisation de \<seealso> , consultez.

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
