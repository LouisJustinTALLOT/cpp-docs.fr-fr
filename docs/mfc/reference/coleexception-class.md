---
description: 'En savoir plus sur : classe COleException'
title: COleException, classe
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: cb11e9c285180c6e54701c210c5329714d7dccb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227089"
---
# <a name="coleexception-class"></a>COleException, classe

Représente une condition d'exception liée à une opération OLE.

## <a name="syntax"></a>Syntaxe

```
class COleException : public CException
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleException ::P tionnaire](#process)|Convertit une exception interceptée en code de retour OLE.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleException :: m_sc](#m_sc)|Contient le code d’État qui indique la raison de l’exception.|

## <a name="remarks"></a>Notes

La `COleException` classe inclut un membre de données public qui contient le code d’état indiquant la raison de l’exception.

En général, vous ne devez pas créer un `COleException` objet directement ; à la place, vous devez appeler [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Pour plus d’informations sur les exceptions, consultez les articles [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et [exceptions : exceptions OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a> COleException :: m_sc

Ce membre de données contient le code d’État OLE qui indique la raison de l’exception.

```
SCODE m_sc;
```

### <a name="remarks"></a>Notes

La valeur de cette variable est définie par [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Pour plus d’informations sur SCODE, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) in the SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a> COleException ::P tionnaire

Appelez la fonction membre **Process** pour convertir une exception interceptée en code d’État OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Paramètres

*pAnyException*<br/>
Pointeur vers une exception interceptée.

### <a name="return-value"></a>Valeur renvoyée

Code d’État OLE.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction est **`static`** .

Pour plus d’informations sur SCODE, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) in the SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Voir aussi

[Exemple MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException (classe)](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
