---
title: Utilisation du CArchive &lt; &lt; et &gt; &gt; des Opérateurs
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368959"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Utilisation du CArchive &lt; &lt; et &gt; &gt; des Opérateurs

`CArchive`fournit des \< opérateurs de <et de >> pour la `CObject`rédaction et la lecture de types de données simples ainsi que s à et à partir d’un fichier.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Pour stocker un objet dans un fichier via une archive

1. L’exemple suivant montre comment stocker un objet dans un fichier via une archive :

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Charger un objet à partir d’une valeur précédemment stockée dans un fichier

1. L’exemple suivant montre comment charger un objet à partir d’une valeur précédemment stockée dans un fichier :

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Habituellement, vous stockez et chargez des données `Serialize` à l’aide d’un fichier via une archive dans les fonctions des `CObject`classes dérivées, que vous devez avoir déclarées avec la macro DECLARE_SERIALIZE. Une référence `CArchive` à un objet `Serialize` est transmise à votre fonction. Vous appelez `IsLoading` la `CArchive` fonction de l’objet pour déterminer si la `Serialize` fonction a été appelée pour charger les données du fichier ou stocker des données au fichier.

La `Serialize` fonction d’une `CObject`classe sérialisable a généralement la forme suivante :

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Le modèle de code ci-dessus est exactement le `Serialize` même que celui qu’AppWizard crée pour la fonction du document (une classe dérivée de `CDocument`). Ce modèle de code vous aide à écrire du code qui est plus facile à examiner, car le code de stockage et le code de chargement doivent toujours être parallèles, comme dans l’exemple suivant :

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La bibliothèque ** < ** définit **>>** et `CArchive` les opérateurs pour comme le premier opérande et les types de données et les types de classe suivants comme le deuxième opéra :

||||
|-|-|-|
|`CObject*`|**SIZE** et`CSize`|**Flotteur**|
|**Mot**|`CString`|**POINT** et`CPoint`|
|`DWORD`|**Octet**|`RECT` et `CRect`|
|**Double**|**Long**|`CTime` et `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> Le stockage `CObject`et le chargement de s via une archive nécessitent une considération supplémentaire. Pour plus d’informations, voir [Stockage et Chargement CObjects via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Les <**>>** `CArchive` ** \< ** et les opérateurs carchifs retournent toujours une référence à l’objet, qui est le premier opérande. Cela vous permet d’enchaîner les opérateurs, comme illustré ci-dessous:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
