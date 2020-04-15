---
title: Classe COleException
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
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375011"
---
# <a name="coleexception-class"></a>Classe COleException

Représente une condition d'exception liée à une opération OLE.

## <a name="syntax"></a>Syntaxe

```
class COleException : public CException
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleException::Process](#process)|Traduit une exception prise en code de retour OLE.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Contient le code d’état qui indique la raison de l’exception.|

## <a name="remarks"></a>Notes

Le `COleException` groupe comprend un membre public des données qui détient le code d’état indiquant la raison de l’exception.

En général, vous ne `COleException` devez pas créer un objet directement; au lieu de cela, vous devriez appeler [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Pour plus d’informations sur les exceptions, voir les articles [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions: OLE Exceptions](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException::m_sc

Ce membre des données détient le code de statut OLE qui indique la raison de l’exception.

```
SCODE m_sc;
```

### <a name="remarks"></a>Notes

La valeur de cette variable est définie par [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Pour plus d’informations sur SCODE, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::Process

Appelez la fonction **membre du processus** pour traduire une exception attrapée en code de statut OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Paramètres

*pAnyException (en anglais)*<br/>
Pointeur à une exception attrapée.

### <a name="return-value"></a>Valeur de retour

Un code de statut OLE.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette fonction est **statique**.

Pour plus d’informations sur SCODE, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
