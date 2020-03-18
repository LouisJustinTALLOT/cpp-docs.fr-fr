---
title: Utilisation des opérateurs de &gt; CArchive &lt;&lt; et &gt;
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442178"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Utilisation des opérateurs de &gt; CArchive &lt;&lt; et &gt;

`CArchive` fournit < opérateurs de\< et de > > pour écrire et lire des types de données simples, ainsi que `CObject`s vers et à partir d’un fichier.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Pour stocker un objet dans un fichier via une archive

1. L’exemple suivant montre comment stocker un objet dans un fichier par le biais d’une archive :

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Pour charger un objet à partir d’une valeur précédemment stockée dans un fichier

1. L’exemple suivant montre comment charger un objet à partir d’une valeur précédemment stockée dans un fichier :

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

En règle générale, vous stockez et chargez des données vers et à partir d’un fichier via une archive dans les fonctions `Serialize` des classes dérivées de `CObject`, que vous devez avoir déclarées avec la macro DECLARE_SERIALIZE. Une référence à un objet `CArchive` est passée à votre fonction `Serialize`. Vous appelez la fonction `IsLoading` de l’objet `CArchive` pour déterminer si la fonction `Serialize` a été appelée pour charger des données à partir du fichier ou stocker des données dans le fichier.

La fonction `Serialize` d’une classe sérialisable `CObject`dérivée se présente généralement sous la forme suivante :

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Le modèle de code ci-dessus est exactement le même que celui créé par AppWizard pour la fonction `Serialize` du document (une classe dérivée de `CDocument`). Ce modèle de code vous aide à écrire du code plus facile à examiner, car le code de stockage et le code de chargement doivent toujours être parallèles, comme dans l’exemple suivant :

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

La bibliothèque définit **<opérateurs \<** et **>>** pour `CArchive` en tant que premier opérande et les types de données et types de classe suivants comme second opérande :

||||
|-|-|-|
|`CObject*`|**Taille** et `CSize`|**float**|
|**WORD**|`CString`|**Point** et `CPoint`|
|`DWORD`|**BYTE**|`RECT` et `CRect`|
|**Double**|**LONG**|`CTime` et `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Le stockage et le chargement de `CObject`s via une archive nécessitent une attention particulière. Pour plus d’informations, consultez [stockage et chargement de CObjects via une archive](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Les opérateurs **< CArchive\<** et **>>** renvoient toujours une référence à l’objet `CArchive`, qui est le premier opérande. Cela vous permet de chaîner les opérateurs, comme illustré ci-dessous :

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Sérialisation : sérialisation d’un objet](../mfc/serialization-serializing-an-object.md)
