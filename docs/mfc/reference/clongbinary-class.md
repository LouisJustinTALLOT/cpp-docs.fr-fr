---
description: 'En savoir plus sur : CLongBinary, classe'
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
ms.openlocfilehash: ad6836ce6ee7e95929f69d226dcab61fc5482277
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336714"
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
|[CLongBinary :: CLongBinary](#clongbinary)|Construit un objet `CLongBinary`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CLongBinary :: m_dwDataLength](#m_dwdatalength)|Contient la taille réelle, en octets, de l’objet de données dont le handle est stocké dans `m_hData` .|
|[CLongBinary :: m_hData](#m_hdata)|Contient un handle Windows HGLOBAL vers l’objet image réel.|

## <a name="remarks"></a>Notes

Par exemple, un champ d’enregistrement dans une table SQL peut contenir une bitmap représentant une image. Un `CLongBinary` objet stocke un tel objet et effectue le suivi de sa taille.

> [!NOTE]
> En général, il est recommandé d’utiliser [CByteArray](../../mfc/reference/cbytearray-class.md) conjointement avec la fonction [DFX_Binary](record-field-exchange-functions.md#dfx_binary) . Vous pouvez toujours utiliser `CLongBinary` , mais en général, `CByteArray` il offre davantage de fonctionnalités sous Win32, car il n’y a plus de limite de taille rencontrée avec 16 bits `CByteArray` . Ce Conseil s’applique à la programmation avec DAO (Data Access Objects), ainsi qu’à Open Database Connectivity (ODBC).

Pour utiliser un `CLongBinary` objet, déclarez un membre de données de champ de type `CLongBinary` dans votre classe de Recordset. Ce membre sera un membre incorporé de la classe Recordset et sera construit lors de la construction du Recordset. Une fois l' `CLongBinary` objet construit, le mécanisme RFX (Record Field Exchange) charge l’objet de données à partir d’un champ de l’enregistrement actif sur la source de données et le stocke dans l’enregistrement lorsque l’enregistrement est mis à jour. RFX interroge la source de données pour la taille de l’objet binaire volumineux, lui alloue du stockage (via le `CLongBinary` membre de données de l’objet `m_hData` ) et stocke un `HGLOBAL` handle aux données dans `m_hData` . RFX stocke également la taille réelle de l’objet de données dans le `m_dwDataLength` membre de données. Travaillez avec les données de l’objet via `m_hData` , en utilisant les mêmes techniques que celles que vous utiliseriez normalement pour manipuler les données stockées dans un `HGLOBAL` handle Windows.

Lorsque vous détruisez votre jeu d’enregistrements, l’objet incorporé `CLongBinary` est également détruit et son destructeur libère le `HGLOBAL` descripteur de données.

Pour plus d’informations sur les objets volumineux et l’utilisation de `CLongBinary` , consultez les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) et [Recordset : utilisation d’éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdb_. h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a> CLongBinary :: CLongBinary

Construit un objet `CLongBinary`.

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a> CLongBinary :: m_dwDataLength

Stocke la taille réelle, en octets, des données stockées dans le handle HGLOBAL dans `m_hData` .

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Notes

Cette taille peut être inférieure à la taille du bloc de mémoire alloué aux données. Appelez la fonction Win32 [GLobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) pour récupérer la taille allouée.

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a> CLongBinary :: m_hData

Stocke un descripteur HGLOBAL Windows aux données réelles de l’objet BLOB.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
