---
description: 'En savoir plus sur : &lt; Résumé&gt;'
title: '&lt;Résumé> (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 3003a3226a67d864be1a07a47151e7003c5514a4
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126336"
---
# <a name="ltsummarygt"></a>&lt;summary&gt;

La \<summary> balise doit être utilisée pour décrire un type ou un membre de type. Utilisez [\<remarks>](remarks-visual-cpp.md) pour ajouter des informations supplémentaires à une description de type.

## <a name="syntax"></a>Syntaxe

```
<summary>description</summary>
```

#### <a name="parameters"></a>Paramètres

*description*<br/>
Résumé de l’objet.

## <a name="remarks"></a>Notes

Le texte de la \<summary> balise est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans l' [Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport Web de commentaire de code.

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour traiter les commentaires de documentation dans un fichier.

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
