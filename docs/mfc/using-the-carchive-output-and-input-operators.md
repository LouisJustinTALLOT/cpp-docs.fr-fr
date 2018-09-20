---
title: À l’aide de CArchive &lt; &lt; et &gt; &gt; opérateurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49ea94258c163c241243934f41d55d896d0d1fa2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372455"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>À l’aide de CArchive &lt; &lt; et &gt; &gt; opérateurs

`CArchive` Fournit des <\< et >> opérateurs pour écrire et lire des types de données simples, ainsi que `CObject`s vers et à partir d’un fichier.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Pour stocker un objet dans un fichier via une archive

1. L’exemple suivant montre comment stocker un objet dans un fichier via une archive :

     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Charger un objet à partir d’une valeur précédemment stockée dans un fichier

1. L’exemple suivant montre comment charger un objet à partir d’une valeur précédemment stockée dans un fichier :

     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

En règle générale, vous stockez et charger des données vers et à partir d’un fichier via une archive située dans le `Serialize` fonctions de `CObject`-les classes dérivées, qui vous devez avoir déclaré CObject. Une référence à un `CArchive` objet est passé à votre `Serialize` (fonction). Vous appelez le `IsLoading` fonction de la `CArchive` objet pour déterminer si le `Serialize` fonction a été appelée pour charger des données à partir du fichier ou stocker des données dans le fichier.

Le `Serialize` fonction d’un sérialisable `CObject`-classe dérivée a généralement la forme suivante :

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Le modèle de code ci-dessus est exactement le même que celle créée par AppWizard pour la `Serialize` fonction du document (une classe dérivée de `CDocument`). Ce modèle vous permet d’écrire du code qui est plus facile de passer en revue, étant donné que le code de stockage et de chargement doivent toujours être parallèles, comme dans l’exemple suivant :

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La bibliothèque définit **< \<** et **>>** opérateurs pour `CArchive` en tant que le premier opérande et les types de données suivants et les types de classe en tant que le second opérande :

||||
|-|-|-|
|`CObject*`|**TAILLE** et `CSize`|**float**|
|**WORD**|`CString`|**POINT** et `CPoint`|
|`DWORD`|**BYTE**|`RECT` et `CRect`|
|**Double**|**LONG**|`CTime` et `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Stockage et chargement `CObject`via une archive nécessite un examen supplémentaire. Pour plus d’informations, consultez [stockage et chargement d’objets CObject via une Archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Le **CArchive <\<**  et **>>** opérateurs retournent toujours une référence à la `CArchive` objet, qui est le premier opérande. Cela vous permet de chaîner les opérateurs, comme illustré ci-dessous :

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)

