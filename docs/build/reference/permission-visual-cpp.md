---
title: '&lt;autorisation > (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: 764048f7bc579afa6862bdff40968588955dc307
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825579"
---
# <a name="ltpermissiongt"></a>&lt;permission&gt;

La balise \<permission> vous permet de documenter l’accès d’un membre. <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.

## <a name="syntax"></a>Syntaxe

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Paramètres

*member*<br/>
Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.  Mettez le nom entre guillemets simples ou doubles.

Le compilateur émet un avertissement s'il ne trouve pas `member`.

Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](see-visual-cpp.md).

*description*<br/>
Description de l’accès au membre.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

Le compilateur MSVC tentera de résoudre les références cref en une seule passe via les commentaires de documentation.  Par conséquent, si lorsque vous utilisez les règles de recherche C++, un symbole est introuvable par le compilateur, la référence est marquée comme non résolue. Pour plus d’informations, consultez [\<seealso>](seealso-visual-cpp.md).

## <a name="example"></a>Exemple

```
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
