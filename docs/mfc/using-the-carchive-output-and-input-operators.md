---
description: 'En savoir plus sur : utilisation des &lt; &lt; opérateurs CArchive et &gt; &gt;'
title: Utilisation des &lt; &lt; opérateurs CArchive et &gt; &gt;
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: a3e6d65ac2ff024f779edb6d23a43f7331628c3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314566"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Utilisation des &lt; &lt; opérateurs CArchive et &gt; &gt;

`CArchive` fournit \< and > des opérateurs de <> pour l’écriture et la lecture de types de données simples, ainsi que de `CObject` s vers et à partir d’un fichier.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Pour stocker un objet dans un fichier via une archive

1. L’exemple suivant montre comment stocker un objet dans un fichier par le biais d’une archive :

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Pour charger un objet à partir d’une valeur précédemment stockée dans un fichier

1. L’exemple suivant montre comment charger un objet à partir d’une valeur précédemment stockée dans un fichier :

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

En règle générale, vous stockez et chargez des données vers et à partir d’un fichier via une archive dans les `Serialize` fonctions des `CObject` classes dérivées de, que vous devez avoir déclarées avec la macro DECLARE_SERIALIZE. Une référence à un `CArchive` objet est passée à votre `Serialize` fonction. Vous appelez la `IsLoading` fonction de l' `CArchive` objet pour déterminer si la `Serialize` fonction a été appelée pour charger des données à partir du fichier ou stocker des données dans le fichier.

La `Serialize` fonction d’une `CObject` classe dérivée sérialisable se présente généralement sous la forme suivante :

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Le modèle de code ci-dessus est exactement le même que celui créé par AppWizard pour la `Serialize` fonction du document (classe dérivée de `CDocument` ). Ce modèle de code vous aide à écrire du code plus facile à examiner, car le code de stockage et le code de chargement doivent toujours être parallèles, comme dans l’exemple suivant :

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La bibliothèque définit **`<<`** les **`>>`** opérateurs et pour `CArchive` comme premier opérande, ainsi que les types de données et les types de classe suivants comme second opérande :

:::row:::
   :::column span="":::
      `BYTE`\
      `CObject*`\
      `COleCurrency`\
      `COleDateTime`\
      `COleDateTimeSpan`
   :::column-end:::
   :::column span="":::
      `COleVariant`\
      `CString`\
      `CTime` et `CTimeSpan`\
      `Double`
   :::column-end:::
   :::column span="":::
      `DWORD`\
      `Float`\
      `Int`\
      `LONG`
   :::column-end:::
   :::column span="":::
      `POINT` et `CPoint`\
      `RECT` et `CRect`\
      `SIZE` et `CSize`\
      `WORD`
   :::column-end:::
:::row-end:::

> [!NOTE]
> Le stockage et le chargement des `CObject` s via une archive nécessitent une attention particulière. Pour plus d’informations, consultez [stockage et chargement de CObjects via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Les `CArchive` **`<<`** **`>>`** opérateurs et retournent toujours une référence à l' `CArchive` objet, qui est le premier opérande. Cela vous permet de chaîner les opérateurs, comme illustré ci-dessous :

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
