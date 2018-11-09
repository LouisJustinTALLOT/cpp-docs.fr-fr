---
title: '&lt;para&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C++ XML tag
- para C++ XML tag
ms.assetid: 35f2a1b3-bc14-4f13-bcb0-c39ccbf74d59
ms.openlocfilehash: c9b7316a32001a1e935f064cdd496d6ce350fa30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618138"
---
# <a name="ltparagt-visual-c"></a>&lt;para&gt; (Visual C++)

La balise \<para> est prévue pour une utilisation à l’intérieur d’une balise, telle que [ \<summary>](../ide/summary-visual-cpp.md), [\<remarks>](../ide/remarks-visual-cpp.md) ou [ \<returns>](../ide/returns-visual-cpp.md), et vous permet d’ajouter une structure au texte.

## <a name="syntax"></a>Syntaxe

```
<para>content</para>
```

#### <a name="parameters"></a>Paramètres

*content*<br/>
Texte du paragraphe.

## <a name="remarks"></a>Notes

Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

Consultez [\<summary>](../ide/summary-visual-cpp.md) pour obtenir un exemple d’utilisation de \<para>.

## <a name="see-also"></a>Voir aussi

[Documentation XML](../ide/xml-documentation-visual-cpp.md)