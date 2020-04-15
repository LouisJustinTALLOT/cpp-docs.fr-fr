---
title: CLongBinary, classe
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
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370134"
---
# <a name="clongbinary-class"></a>CLongBinary, classe

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
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Contient la taille réelle dans les octets de `m_hData`l’objet de données dont la poignée est stockée dans .|
|[CLongBinary::m_hData](#m_hdata)|Contient une poignée Windows HGLOBAL à l’objet d’image réelle.|

## <a name="remarks"></a>Notes

Par exemple, un champ d’enregistrement dans une table SQL peut contenir une bitmap représentant une image. Un `CLongBinary` objet stocke un tel objet et garde une trace de sa taille.

> [!NOTE]
> En général, il est préférable maintenant d’utiliser [CByteArray](../../mfc/reference/cbytearray-class.md) en conjonction avec la fonction [DFX_Binary.](record-field-exchange-functions.md#dfx_binary) Vous pouvez `CLongBinary`toujours utiliser `CByteArray` , mais en général fournit plus de fonctionnalités sous Win32, `CByteArray`car il n’y a plus la limitation de taille rencontrée avec 16 bits . Ce conseil s’applique à la programmation avec data Access Objects (DAO) ainsi qu’à la connectivité open Database (ODBC).

Pour utiliser `CLongBinary` un objet, déclarez `CLongBinary` un membre des données de terrain de type dans votre classe de recordet. Ce membre sera un membre intégré de la classe de l’enregistrement et sera construit lorsque le recordet sera construit. Une `CLongBinary` fois l’objet construit, le mécanisme d’échange de champ record (RFX) charge l’objet de données à partir d’un champ dans l’enregistrement actuel sur la source de données et le stocke de nouveau à l’enregistrement lorsque l’enregistrement est mis à jour. RFX interroge la source de données pour la taille du grand objet `CLongBinary` binaire, `m_hData` alloue le `HGLOBAL` stockage pour `m_hData`elle (via le membre des données de l’objet), et stocke une poignée aux données en . RFX stocke également la taille réelle `m_dwDataLength` de l’objet de données dans le membre des données. Travaillez avec les données `m_hData`de l’objet à travers, en utilisant les `HGLOBAL` mêmes techniques que vous utiliseriez normalement pour manipuler les données stockées dans une poignée Windows.

Lorsque vous détruisez votre `CLongBinary` jeu d’enregistrement, l’objet intégré est `HGLOBAL` également détruit, et son destructeur traite la poignée de données.

Pour plus d’informations sur `CLongBinary`les grands objets et l’utilisation de , voir les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) et [Recordset: Working with Large Data Items (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary

Construit un objet `CLongBinary`.

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

Stocke la taille réelle dans les octets des `m_hData`données stockées dans la poignée HGLOBAL dans .

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Notes

Cette taille peut être plus petite que la taille du bloc de mémoire alloué pour les données. Appelez la fonction Win32 [GLobalSize](/windows/win32/api/winbase/nf-winbase-globalsize) pour obtenir la taille allouée.

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary::m_hData

Stocke une poignée Windows HGLOBAL aux données binaires réelles de gros objets.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
