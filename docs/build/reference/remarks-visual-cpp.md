---
title: '&lt;remarks > (commentaires de documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 0d0c63d55de80f498498a6873dacb5e83fc956b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319159"
---
# <a name="ltremarksgt"></a>&lt;remarks&gt;

La balise \<remarks> permet d’ajouter des informations sur un type en complétant les informations spécifiées par [\<summary>](summary-visual-cpp.md). Ces informations sont affichées dans [l’Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code) et dans le rapport web de commentaire de code.

## <a name="syntax"></a>Syntaxe

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Paramètres

*description*<br/>
Description du membre.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
