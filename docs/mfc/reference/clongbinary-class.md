---
title: CLongBinary (classe)
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: ed3a153ec89785a9c9da43037d20f7d88b5661ff
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260710"
---
# <a name="clongbinary-class"></a>CLongBinary (classe)

Simplifie l'utilisation d'objets de données binaires de très grande taille (souvent appelés BLOB ou « objets blob ») dans une base de données.

## <a name="syntax"></a>Syntaxe

```
class CLongBinary : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Construit un objet `CLongBinary`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Contient la taille réelle en octets de l’objet de données dont le handle est stocké dans `m_hData`.|
|[CLongBinary::m_hData](#m_hdata)|Contient un handle Windows HGLOBAL à l’objet de l’image réelle.|

## <a name="remarks"></a>Notes

Par exemple, un champ d’enregistrement dans une table SQL peut contenir une image bitmap représentant une image. Un `CLongBinary` objet stocke un tel objet et effectue le suivi de sa taille.

> [!NOTE]
>  En règle générale, il est préférable désormais à utiliser [CByteArray](../../mfc/reference/cbytearray-class.md) conjointement avec la [DFX_Binary](record-field-exchange-functions.md#dfx_binary) (fonction). Vous pouvez toujours utiliser `CLongBinary`, mais en général `CByteArray` fournit davantage de fonctionnalités sous Win32, dans la mesure où il n’est plus la limite de taille a rencontré avec 16 bits `CByteArray`. Ce Conseil s’applique à la programmation avec des objets DAO (Data Access) ainsi que la connectivité ODBC (Open Database).

Pour utiliser un `CLongBinary` objet, déclarez un membre de données de champ de type `CLongBinary` dans votre classe de jeu d’enregistrements. Ce membre sera un membre incorporé de la classe de jeu d’enregistrements et est créé lorsque le jeu d’enregistrements est construit. Après le `CLongBinary` objet est construit, le mécanisme record field exchange (RFX) charge de l’objet de données à partir d’un champ dans l’enregistrement actif sur la source de données et stocke à l’enregistrement lorsque l’enregistrement est mis à jour. RFX interroge la source de données pour la taille de l’objet BLOB, pour qu’il alloue du stockage (via le `CLongBinary` l’objet `m_hData` membre de données) et stocke un `HGLOBAL` gérer aux données dans `m_hData`. RFX stocke également la taille réelle de l’objet de données dans le `m_dwDataLength` membre de données. Utiliser les données dans l’objet via `m_hData`, utilisant les mêmes techniques que vous utiliseriez normalement pour manipuler les données stockées dans un Windows `HGLOBAL` gérer.

Lorsque vous détruisez le jeu d’enregistrements, incorporée `CLongBinary` également détruit et son destructeur libère la `HGLOBAL` données handle.

Pour plus d’informations sur les objets de grande taille et l’utilisation de `CLongBinary`, consultez les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) et [jeu d’enregistrements : Utilisation des éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdb_.h

##  <a name="clongbinary"></a>  CLongBinary::CLongBinary

Construit un objet `CLongBinary`.

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

Stocke la taille réelle en octets des données stockées dans le descripteur HGLOBAL dans `m_hData`.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Notes

Cette taille peut être inférieure à la taille du bloc de mémoire alloué pour les données. Appelez Win32 [GLobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize) fonction pour obtenir la taille allouée.

##  <a name="m_hdata"></a>  CLongBinary::m_hData

Stocke un handle Windows HGLOBAL pour les données d’objet BLOB réel.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)
