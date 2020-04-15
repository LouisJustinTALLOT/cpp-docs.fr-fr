---
title: Échange de données de boîtes de dialogue pour CRecordView et CDaoRecordView
ms.date: 09/17/2019
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365775"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Échange de données de boîtes de dialogue pour CRecordView et CDaoRecordView

Ce sujet répertorie les fonctions DDX_Field utilisées pour échanger des données entre un [formulaire CRecordset](../../mfc/reference/crecordset-class.md) et un formulaire [CRecordView](../../mfc/reference/crecordview-class.md) ou un [formulaire CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) et un formulaire [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) DAO est utilisé avec les bases de données Access et est pris en charge par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète.

> [!NOTE]
> DDX_Field fonctions sont comme les fonctions DDX en ce qu’elles échangent des données avec des contrôles sous une forme. Mais contrairement à DDX, ils échangent des données avec les champs de l’objet de l’ensemble de disques associé de la vue plutôt qu’avec les champs de la vue d’enregistrement elle-même. Pour plus d’informations, voir les cours `CRecordView` et `CDaoRecordView`.

### <a name="ddx_field-functions"></a>fonctions DDX_Field

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfère les données intégrées entre un membre des données de champ de recordset et l’index de la sélection actuelle dans une boîte combo dans un [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Transfère les `CString` données entre un membre des données de `CRecordView` `CDaoRecordView`champ de recordset et le contrôle de modification d’une boîte combo dans un ou . Lors du déplacement des données de l’ensemble d’enregistrements vers le contrôle, cette fonction sélectionne l’élément dans la boîte combo qui commence avec les caractères de la chaîne spécifiée.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Transfère les `CString` données entre un membre des données de `CRecordView` `CDaoRecordView`champ de recordset et le contrôle de modification d’une boîte combo dans un ou . Lors du déplacement des données de l’ensemble d’enregistrements vers le contrôle, cette fonction sélectionne l’élément dans la boîte combo qui correspond exactement à la chaîne spécifiée.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfère les données Boolean entre un membre `CRecordView` des `CDaoRecordView`données de champ de recordset et une case à cocher dans un ou .|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfère les données integer entre un membre des données de champ `CRecordView` `CDaoRecordView`de recordset et l’index de la sélection actuelle dans une boîte de liste dans un ou .|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Gère le transfert des données [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre un contrôle de liste et les membres des données sur le terrain d’un jeu d’enregistrement. Lors du déplacement des données de l’ensemble d’enregistrements vers le contrôle, cette fonction sélectionne l’élément dans la boîte de liste qui commence avec les caractères de la chaîne spécifiée.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Gère le `CString` transfert de données entre un contrôle de liste et les membres des données sur le terrain d’un jeu d’enregistrement. Lors du déplacement des données de l’ensemble d’enregistrements vers le contrôle, cette fonction sélectionne le premier élément qui correspond exactement à la chaîne spécifiée.|
|[DDX_FieldRadio](#ddx_fieldradio)|Transfère les données d’un groupe de données sur le `CRecordView` `CDaoRecordView`terrain et un groupe de boutons radio dans un ou .|
|[DDX_FieldScroll](#ddx_fieldscroll)|Définit ou obtient la position de défilement d’un contrôle de barre de défilement dans un `CRecordView` ou `CDaoRecordView`. Appelez de votre fonction [DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronise la position du pouce d’un contrôle `int` de curseur dans une vue d’enregistrement et un membre des données sur le terrain d’un ensemble d’enregistrements. |
|[DDX_FieldText](#ddx_fieldtext)|Les versions surchargées sont `int`disponibles pour le `DWORD`transfert , **UINT**, **long**, , [CString](../../atl-mfc-shared/reference/cstringt-class.md), **flotteur**, **double**, **court**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), et les données [COleCurrency](../../mfc/reference/colecurrency-class.md) entre un membre des données de champ recordet et une boîte de modification dans un `CRecordView` ou `CDaoRecordView`.|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

La `DDX_FieldCBIndex` fonction synchronise l’index de l’élément sélectionné dans le contrôle de `int` la boîte de liste d’un contrôle de boîte combo dans une vue d’enregistrement et un membre des données de champ d’un ensemble d’enregistrements associé à la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*index*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données de l’ensemble d’enregistrements au contrôle, cette fonction définit la sélection dans le contrôle en fonction de la valeur spécifiée dans *l’index*. Lors d’un transfert de l’ensemble d’enregistrements au contrôle, si le champ de l’enregistrement est Null, MFC définit la valeur de l’index à 0. Lors d’un transfert du contrôle à l’ensemble d’enregistrements, si le contrôle est vide ou si aucun élément n’est sélectionné, le champ de l’enregistrement est réglé à 0.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. L’exemple serait `DDX_FieldCBIndex`similaire pour .

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

La `DDX_FieldCBString` fonction gère le transfert des données [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre le contrôle de `CString` modification d’un contrôle de boîte combo dans une vue d’enregistrement et un membre des données de terrain d’un ensemble d’enregistrements associé à la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données de l’enregistrement au contrôle, cette fonction définit la sélection actuelle dans la boîte combo à la première rangée qui commence avec les caractères de la chaîne spécifiée en *valeur*. Lors d’un transfert de l’ensemble d’enregistrements au contrôle, si le champ de recordet est Null, toute sélection est supprimée de la boîte combo et le contrôle de modification de la boîte combo est réglé pour vider. Lors d’un transfert du contrôle au recordet, si le contrôle est vide, le champ de la série de records est réglé à Null si le champ le permet.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. L’exemple comprend `DDX_FieldCBString`un appel à .

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

La `DDX_FieldCBStringExact` fonction gère le transfert des données [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre le contrôle de `CString` modification d’un contrôle de boîte combo dans une vue d’enregistrement et un membre des données de terrain d’un ensemble d’enregistrements associé à la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données de l’enregistrement au contrôle, cette fonction définit la sélection actuelle dans la boîte combo à la première rangée qui correspond exactement à la chaîne spécifiée en *valeur*. Lors d’un transfert de l’ensemble d’enregistrements au contrôle, si le champ de recordset est NULL, toute sélection est supprimée de la boîte combo et la boîte d’édition de la boîte combo est définie pour vider. Lors d’un transfert du contrôle au recordet, si le contrôle est vide, le champ de recordset est réglé à NULL.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. Appels `DDX_FieldCBStringExact` à serait similaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

La `DDX_FieldCheck` fonction gère le transfert de données **int** entre un contrôle de case à cocher dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre des données **int** de la boîte de dialogue, la vue de forme, ou l’objet de vue de commande.

```cpp
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la case à cocher associé à la propriété de commande.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_FieldCheck` l’appelle, la *valeur* est réglée à l’état actuel du contrôle de la case à cocher, ou l’état du contrôle est réglé pour *la valeur*, selon la direction du transfert.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

La `DDX_FieldLBIndex` fonction synchronise l’index de l’élément sélectionné dans un contrôle de boîte de liste dans une vue d’enregistrement et un membre des données sur le champ **int** d’un ensemble d’enregistrements associé à la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*index*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données de l’ensemble d’enregistrements au contrôle, cette fonction définit la sélection dans le contrôle en fonction de la valeur spécifiée dans *l’index*. Lors d’un transfert de l’ensemble d’enregistrements au contrôle, si le champ de l’enregistrement est Null, MFC définit la valeur de l’index à 0. Sur un transfert de contrôle à recordet, si le contrôle est vide, le champ recordet est réglé à 0.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

Les `DDX_FieldLBString` copies de la sélection actuelle d’un contrôle de boîte de liste dans une vue d’enregistrement à un membre des données de terrain [CString](../../atl-mfc-shared/reference/cstringt-class.md) d’un ensemble d’enregistrements associé à la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Dans la direction inverse, cette fonction définit la sélection actuelle dans la boîte de liste à la première rangée qui commence avec les caractères de la chaîne spécifiée par *la valeur*. Lors d’un transfert de l’enregistrement au contrôle, si le champ de la liste des enregistrements est nul, toute sélection est supprimée de la boîte de liste. Lors d’un transfert du contrôle au recordet, si le contrôle est vide, le champ de recordset est réglé à Null.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. Appels `DDX_FieldLBString` à serait similaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

La `DDX_FieldLBStringExact` fonction copie la sélection actuelle d’un contrôle de boîte de liste dans une vue d’enregistrement à un membre des données de terrain [CString](../../atl-mfc-shared/reference/cstringt-class.md) d’un ensemble d’enregistrements associé à la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Dans la direction inverse, cette fonction définit la sélection actuelle dans la boîte de liste à la première rangée qui correspond exactement à la chaîne spécifiée en *valeur*. Lors d’un transfert de l’enregistrement au contrôle, si le champ de la liste des enregistrements est nul, toute sélection est supprimée de la boîte de liste. Lors d’un transfert du contrôle au recordet, si le contrôle est vide, le champ de recordset est réglé à Null.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. Appels `DDX_FieldLBStringExact` à serait similaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

La `DDX_FieldRadio` fonction associe une variable de membre **int** à base zéro de l’ensemble d’enregistrements d’une vue d’enregistrement avec le bouton radio actuellement sélectionné dans un groupe de boutons radio dans la vue d’enregistrement.

```cpp
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID du premier d’un groupe (avec style WS_GROUP) de commandes de bouton radio adjacentes dans [l’objet CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du transfert du champ de l’enregistrement à la vue, cette fonction allume le bouton radio *nth* (zéro à base) et éteint les autres boutons. Dans la direction inverse, cette fonction définit le champ de recordset au nombre ordinaire du bouton radio qui est actuellement allumé (vérifié). Lors d’un transfert de l’enregistrement au contrôle, si le champ de la salle d’enregistrement est null, aucun bouton n’est sélectionné. Lors d’un transfert du contrôle à l’ensemble des enregistrements, si aucun contrôle n’est sélectionné, le champ de recordet est réglé à Null si le champ le permet.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. Appels `DDX_FieldRadio` à serait similaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

La `DDX_FieldScroll` fonction synchronise la position de défilement d’un contrôle de barre de défilement dans une vue d’enregistrement et un membre des données de champ **int** d’un ensemble d’enregistrements associé à la vue d’enregistrement (ou avec n’importe quelle variable d’intégreur que vous choisissez de la cartographier).

```cpp
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID du premier d’un groupe (avec style WS_GROUP) de commandes de bouton radio adjacentes dans [l’objet CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données de l’ensemble d’enregistrements vers le contrôle, cette fonction définit la position de défilement du contrôle de la barre de défilement à la valeur spécifiée en *valeur*. Lors d’un transfert de l’enregistrement au contrôle, si le champ de recordset est Null, le contrôle de la barre de défilement est réglé à 0. Lors d’un transfert du contrôle au jeu d’enregistrement, si le contrôle est vide, la valeur du champ de l’enregistrement est de 0.

Utilisez la première version si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième version si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. Appels `DDX_FieldScroll` à serait similaire.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

La `DDX_FieldSlider` fonction synchronise la position du pouce d’un contrôle de curseur dans une vue d’enregistrement et un membre des données **int** field d’un ensemble d’enregistrements associé à la vue d’enregistrement (ou avec n’importe quelle variable d’intégrateur que vous choisissez de la cartographier).

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DDX_FieldSlider(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle du curseur.

*value*<br/>
Une référence à la valeur à échanger. Ce paramètre tient ou sera utilisé pour définir la position actuelle du pouce du contrôle du curseur.

*pRecordset*<br/>
Un pointeur `CRecordset` vers `CDaoRecordset` l’associé ou l’objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données de l’ensemble d’enregistrements vers le curseur, cette fonction définit la position du curseur à la valeur spécifiée en *valeur*. Lors d’un transfert de l’enregistrement au contrôle, si le champ de recordet est Null, la position du contrôle du curseur est réglée à 0. Lors d’un transfert du contrôle vers le jeu d’enregistrement, si le contrôle est vide, la valeur du champ de l’enregistrement est de 0.

`DDX_FieldSlider`n’échange pas d’informations de plage avec des commandes de curseur capables de définir une plage plutôt que simplement une position.

Utilisez la première dérogation de la fonction si vous travaillez avec les classes basées sur l’ODBC. Utilisez la deuxième dérogation avec les classes basées sur le DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../dialog-data-exchange-and-validation.md). Pour des exemples et plus `CRecordView` `CDaoRecordView` d’informations sur DDX pour et les champs, voir [Vues d’enregistrement](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur les commandes de curseurs, voir [à l’aide de CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Exemple

Voir [DDX_FieldText](#ddx_fieldtext) pour un exemple général DDX_Field. Appels `DDX_FieldSlider` à serait similaire.

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

La `DDX_FieldText` fonction gère le transfert de **int**, **court**, **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **flotteur**, **double**, **BOOL**, ou **BYTE** données entre un contrôle de boîte de modification et les membres de données de terrain d’un recordet.

```cpp
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Une référence à un membre `CRecordset` des `CDaoRecordset` données sur le terrain dans l’objet associé ou associé. Le type de valeur de données dépend de `DDX_FieldText` laquelle des versions surchargées de votre utilisation.

*pRecordset*<br/>
Un pointeur de l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées. Ce pointeur permet `DDX_FieldText` de détecter et de définir les valeurs Null.

### <a name="remarks"></a>Notes

Pour les objets [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), `DDX_FieldText` gère également le transfert de valeurs [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)et [COleCurrency](../../mfc/reference/colecurrency-class.md) . Un contrôle vide de boîte d’édition indique une valeur Null. Lors d’un transfert de l’ensemble d’enregistrements au contrôle, si le champ de la boîte de disques est Null, la boîte de modification est définie pour vider. Lors d’un transfert du contrôle au recordet, si le contrôle est vide, le champ de recordset est réglé à Null.

Utilisez les versions avec les paramètres [CRecordset](../../mfc/reference/crecordset-class.md) si vous travaillez avec les classes basées sur ODBC. Utilisez les versions avec les paramètres [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) si vous travaillez avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour des exemples et plus d’informations sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView,](../../mfc/reference/cdaorecordview-class.md) voir l’article [Record Views](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

La `DoDataExchange` fonction suivante pour un `DDX_FieldText` [CRecordView](../../mfc/reference/crecordview-class.md) contient `IDC_COURSELIST` des appels de fonction pour trois types de données : est une boîte combo ; les deux autres commandes sont des boîtes d’édition. Pour la programmation DAO, le paramètre *m_pSet* est un pointeur d’un [CRecordset](../../mfc/reference/crecordset-class.md) ou [DUroRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)
