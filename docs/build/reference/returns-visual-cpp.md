---
title: '&lt;Retourne > (commentaires de Documentation C++)'
ms.date: 11/04/2016
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
ms.openlocfilehash: 72a6ad05f3a78919b652f518d11814c3f95c5fd0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318678"
---
# <a name="ltreturnsgt"></a>&lt;returns&gt;

La balise \<returns> doit être utilisée dans le commentaire relatif à une déclaration de méthode pour décrire la valeur de retour.

## <a name="syntax"></a>Syntaxe

```
<returns>description</returns>
```

#### <a name="parameters"></a>Paramètres

*description*<br/>
Description de la valeur de retour.

## <a name="remarks"></a>Notes

Compilez avec [/doc](doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

```
// xml_returns_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_returns_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <returns>Returns zero.</returns>
   int GetZero() { return 0; }
};
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
