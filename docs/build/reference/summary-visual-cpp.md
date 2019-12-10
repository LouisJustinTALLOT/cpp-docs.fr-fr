---
title: '> Résumé des &lt;C++ (commentaires de documentation)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 0620273f24573539897809b7892d46ad49b7aa57
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988585"
---
# <a name="ltsummarygt"></a>&lt;summary&gt;

La balise \<summary> doit être utilisée pour décrire un type ou un membre de type. Utilisez [\<remarks>](remarks-visual-cpp.md) pour ajouter des informations supplémentaires à une description de type.

## <a name="syntax"></a>Syntaxe

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parameters

*description*<br/>
Résumé de l’objet.

## <a name="remarks"></a>Notes

Le texte de la balise \<summary> est la seule source d’informations sur le type dans IntelliSense et il est également affiché dans [l’Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport web de commentaire de code.

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```cpp
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
