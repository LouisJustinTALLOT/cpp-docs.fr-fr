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
ms.openlocfilehash: 48ffe6f124b91ee8ad60452f26d895bc2698779b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447309"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Échange de données de boîtes de dialogue pour CRecordView et CDaoRecordView

Cette rubrique répertorie les fonctions de DDX_Field utilisées pour échanger des données entre un [CRecordset](../../mfc/reference/crecordset-class.md) et une forme [CRecordView](../../mfc/reference/crecordview-class.md) ou une forme [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) et un formulaire [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

> [!NOTE]
>  Les fonctions de DDX_Field sont similaires aux fonctions DDX en ce qu’elles échangent des données avec des contrôles dans un formulaire. Mais contrairement à DDX, ils échangent des données avec les champs de l’objet Recordset associé à la vue plutôt qu’avec les champs de la vue de l’enregistrement proprement dite. Pour plus d’informations, consultez classes `CRecordView` et `CDaoRecordView`.

### <a name="ddx_field-functions"></a>Fonctions DDX_Field

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfère les données de type entier entre un membre de données de champ de Recordset et l’index de la sélection actuelle dans une zone de liste déroulante dans [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Transfère `CString` données entre un membre de données de champ de Recordset et le contrôle d’édition d’une zone de liste déroulante dans un `CRecordView` ou `CDaoRecordView`. Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction sélectionne l’élément dans la zone de liste déroulante qui commence par les caractères de la chaîne spécifiée.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Transfère `CString` données entre un membre de données de champ de Recordset et le contrôle d’édition d’une zone de liste déroulante dans un `CRecordView` ou `CDaoRecordView`. Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction sélectionne l’élément dans la zone de liste déroulante qui correspond exactement à la chaîne spécifiée.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfère des données booléennes entre un membre de données de champ de Recordset et une case à cocher dans un `CRecordView` ou `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfère les données de type entier entre un membre de données de champ de Recordset et l’index de la sélection actuelle dans une zone de liste d’un `CRecordView` ou `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Gère le transfert de données [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre un contrôle de zone de liste et les membres de données de champ d’un jeu d’enregistrements. Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction sélectionne dans la zone de liste l’élément qui commence par les caractères de la chaîne spécifiée.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Gère le transfert de données de `CString` entre un contrôle de zone de liste et les membres de données de champ d’un jeu d’enregistrements. Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction sélectionne le premier élément qui correspond exactement à la chaîne spécifiée.|
|[DDX_FieldRadio](#ddx_fieldradio)|Transfère des données de type entier entre un membre de données de champ de Recordset et un groupe de cases d’option dans un `CRecordView` ou `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Définit ou obtient la position de défilement d’un contrôle de barre de défilement dans un `CRecordView` ou `CDaoRecordView`. Appelez à partir de votre fonction [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) .|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronise la position du curseur d’un contrôle Slider dans une vue d’enregistrement et un membre de données de champ `int` d’un jeu d’enregistrements. |
|[DDX_FieldText](#ddx_fieldtext)|Des versions surchargées sont disponibles pour transférer des données `int`, **uint**, **long**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **short**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)et [COleCurrency](../../mfc/reference/colecurrency-class.md) entre un membre de données de champ de Recordset et une zone d’édition dans un `CRecordView` ou `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

La fonction `DDX_FieldCBIndex` synchronise l’index de l’élément sélectionné dans le contrôle de zone de liste d’un contrôle zone de liste déroulante dans une vue d’enregistrement et un membre de données de champ `int` d’un jeu d’enregistrements associé à la vue d’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*index*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction définit la sélection dans le contrôle en fonction de la valeur spécifiée dans *index*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset est null, MFC affecte la valeur 0 à l’index. Sur un transfert de contrôle à Recordset, si le contrôle est vide ou si aucun élément n’est sélectionné, le champ Recordset a la valeur 0.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. L’exemple est similaire pour `DDX_FieldCBIndex`.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

##  <a name="ddx_fieldcbstring"></a>DDX_FieldCBString

La fonction `DDX_FieldCBString` gère le transfert de données [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une vue d’enregistrement et un membre de données de champ `CString` d’un jeu d’enregistrements associé à la vue d’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction définit la sélection actuelle dans la zone de liste déroulante sur la première ligne qui commence par les caractères de la chaîne spécifiée dans *valeur*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset a la valeur null, toute sélection est supprimée de la zone de liste déroulante et le contrôle d’édition de la zone de liste déroulante est défini sur vide. Sur un transfert de contrôle à Recordset, si le contrôle est vide, le champ Recordset a la valeur null si le champ le permet.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. L’exemple comprend un appel à `DDX_FieldCBString`.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

## <a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

La fonction `DDX_FieldCBStringExact` gère le transfert de données [CString](../../atl-mfc-shared/reference/cstringt-class.md) entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une vue d’enregistrement et un membre de données de champ `CString` d’un jeu d’enregistrements associé à la vue d’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction définit la sélection actuelle dans la zone de liste déroulante sur la première ligne qui correspond exactement à la chaîne spécifiée dans *valeur*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset a la valeur NULL, toute sélection est supprimée de la zone de liste déroulante et la zone d’édition de la zone de liste déroulante est définie sur vide. Sur un transfert de contrôle à Recordset, si le contrôle est vide, le champ Recordset a la valeur NULL.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. Les appels à `DDX_FieldCBStringExact` sont similaires.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="ddx_fieldcheck"></a>DDX_FieldCheck

La fonction `DDX_FieldCheck` gère le transfert de données **int** entre un contrôle de case à cocher dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **int** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de case à cocher associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_FieldCheck` est appelé, la *valeur* est définie sur l’état actuel du contrôle de case à cocher, ou l’état du contrôle est défini sur *valeur*, selon la direction du transfert.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

La fonction `DDX_FieldLBIndex` synchronise l’index de l’élément sélectionné dans un contrôle de zone de liste dans une vue d’enregistrement et un membre de données de champ **int** d’un jeu d’enregistrements associé à la vue d’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*index*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction définit la sélection dans le contrôle en fonction de la valeur spécifiée dans *index*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset est null, MFC affecte la valeur 0 à l’index. Sur un transfert de contrôle à Recordset, si le contrôle est vide, le champ Recordset a la valeur 0.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="ddx_fieldlbstring"></a>DDX_FieldLBString

L' `DDX_FieldLBString` copie la sélection actuelle d’un contrôle de zone de liste dans une vue d’enregistrement vers un membre de données de champ [CString](../../atl-mfc-shared/reference/cstringt-class.md) d’un jeu d’enregistrements associé à la vue d’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Dans le sens inverse, cette fonction définit la sélection actuelle dans la zone de liste sur la première ligne qui commence par les caractères de la chaîne spécifiée par *valeur*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset a la valeur null, toute sélection est supprimée de la zone de liste. Sur un transfert de contrôle à Recordset, si le contrôle est vide, le champ Recordset a la valeur null.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. Les appels à `DDX_FieldLBString` sont similaires.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

La fonction `DDX_FieldLBStringExact` copie la sélection actuelle d’un contrôle de zone de liste dans une vue d’enregistrement sur un membre de données de champ [CString](../../atl-mfc-shared/reference/cstringt-class.md) d’un jeu d’enregistrements associé à la vue d’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Dans le sens inverse, cette fonction définit la sélection actuelle dans la zone de liste sur la première ligne qui correspond exactement à la chaîne spécifiée dans *valeur*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset a la valeur null, toute sélection est supprimée de la zone de liste. Sur un transfert de contrôle à Recordset, si le contrôle est vide, le champ Recordset a la valeur null.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. Les appels à `DDX_FieldLBStringExact` sont similaires.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="ddx_fieldradio"></a>DDX_FieldRadio

La fonction `DDX_FieldRadio` associe une variable de membre **int** de base zéro du Recordset d’une vue de l’enregistrement à la case d’option actuellement sélectionnée dans un groupe de cases d’option de la vue de l’enregistrement.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID du premier dans un groupe (avec le style WS_GROUP) des contrôles de case d’option adjacents dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du transfert du champ Recordset vers la vue, cette fonction active la *nième* case d’option (de base zéro) et désactive les autres boutons. Dans le sens inverse, cette fonction définit le champ Recordset sur le numéro ordinal de la case d’option actuellement activée (cochée). Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset a la valeur null, aucun bouton n’est sélectionné. Sur un transfert de contrôle à Recordset, si aucun contrôle n’est sélectionné, le champ Recordset a la valeur null si le champ le permet.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. Les appels à `DDX_FieldRadio` sont similaires.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="ddx_fieldscroll"></a>DDX_FieldScroll

La fonction `DDX_FieldScroll` synchronise la position de défilement d’un contrôle de barre de défilement dans une vue d’enregistrement et un membre de données de champ **int** d’un jeu d’enregistrements associé à la vue d’enregistrement (ou avec n’importe quelle variable de type entier que vous choisissez de mapper).

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID du premier dans un groupe (avec le style WS_GROUP) des contrôles de case d’option adjacents dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données du jeu d’enregistrements vers le contrôle, cette fonction définit la position de défilement du contrôle de barre de défilement sur la valeur spécifiée dans *valeur*. Lors d’un transfert à partir du recordset vers le contrôle, si le champ de l’ensemble d’enregistrements est null, le contrôle de barre de défilement est défini sur 0. Sur un transfert de contrôle à Recordset, si le contrôle est vide, la valeur du champ Recordset est 0.

Utilisez la première version si vous utilisez les classes ODBC. Utilisez la deuxième version si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. Les appels à `DDX_FieldScroll` sont similaires.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

## <a name="ddx_fieldslider"></a>DDX_FieldSlider

La fonction `DDX_FieldSlider` synchronise la position Thumb d’un contrôle Slider dans une vue d’enregistrement et un membre de données de champ **int** d’un jeu d’enregistrements associé à la vue d’enregistrement (ou avec la variable de type entier que vous choisissez de mapper).

### <a name="syntax"></a>Syntaxe

  ```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle Slider.

*value*<br/>
Référence à la valeur à échanger. Ce paramètre contient ou sera utilisé pour définir la position actuelle du curseur du contrôle Slider.

*pRecordset*<br/>
Pointeur vers l’objet `CRecordset` ou `CDaoRecordset` associé avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données du jeu d’enregistrements vers le curseur, cette fonction définit la position du curseur sur la valeur spécifiée dans *valeur*. Lors d’un transfert de l’objet Recordset vers le contrôle, si le champ Recordset a la valeur null, la position du contrôle Slider est définie sur 0. Sur un transfert du contrôle vers le Recordset, si le contrôle est vide, la valeur du champ du Recordset est 0.

`DDX_FieldSlider` n’échange pas d’informations de plage avec des contrôles Slider permettant de définir une plage plutôt qu’une simple position.

Utilisez la première substitution de la fonction si vous utilisez les classes ODBC. Utilisez la deuxième substitution avec les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs `CRecordView` et `CDaoRecordView`, consultez [vues d’enregistrement](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur les contrôles Slider, consultez [utilisation de CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple de DDX_Field général. Les appels à `DDX_FieldSlider` sont similaires.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

##  <a name="ddx_fieldtext"></a>DDX_FieldText

La fonction `DDX_FieldText` gère le transfert de **données int**, **short**, **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **bool**ou **Byte** entre un contrôle zone d’édition et les données membres de champ d’un jeu d’enregistrements.

```
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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle dans l’objet [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Référence à un membre de données de champ dans l’objet `CRecordset` ou `CDaoRecordset` associé. Le type de données de la valeur dépend de la version surchargée de `DDX_FieldText` que vous utilisez.

*pRecordset*<br/>
Pointeur vers l’objet [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) avec lequel les données sont échangées. Ce pointeur permet à `DDX_FieldText` de détecter et de définir des valeurs NULL.

### <a name="remarks"></a>Notes

Pour les objets [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), `DDX_FieldText` gère également le transfert de valeurs [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)et [COleCurrency](../../mfc/reference/colecurrency-class.md) . Un contrôle de zone d’édition vide indique une valeur null. Lors d’un transfert à partir du recordset vers le contrôle, si le champ Recordset a la valeur null, la zone d’édition est définie sur vide. Sur un transfert de contrôle à Recordset, si le contrôle est vide, le champ Recordset a la valeur null.

Utilisez les versions avec les paramètres [CRecordset](../../mfc/reference/crecordset-class.md) si vous utilisez les classes ODBC. Utilisez les versions avec les paramètres [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) si vous utilisez les classes basées sur DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour obtenir des exemples et des informations supplémentaires sur DDX pour les champs [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) , consultez l’article [affichages des enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

La fonction `DoDataExchange` suivante pour une [CRecordView](../../mfc/reference/crecordview-class.md) contient des appels de fonction `DDX_FieldText` pour trois types de données : `IDC_COURSELIST` est une zone de liste modifiable ; les deux autres contrôles sont des zones d’édition. Pour la programmation DAO, le paramètre *m_pSet* est un pointeur vers un [CRecordset](../../mfc/reference/crecordset-class.md) ou un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)
