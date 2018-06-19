---
title: Classe de COleException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs:
- C++
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46f554e375e8c0185e8c2b75c81eeae5ee615c51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370469"
---
# <a name="coleexception-class"></a>Classe de COleException
Représente une condition d'exception liée à une opération OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleException::Process](#process)|Traduit une exception interceptée dans un code de retour OLE.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|Contient le code d’état qui indique la raison de l’exception.|  
  
## <a name="remarks"></a>Notes  
 La `COleException` classe inclut une donnée membre publique qui contient le code d’état indiquant la raison de l’exception.  
  
 En règle générale, vous ne devez pas créer un `COleException` de l’objet directement ; au lieu de cela, vous devez appeler [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Pour plus d’informations sur les exceptions, consultez les articles [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions : Exceptions OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  
  
##  <a name="m_sc"></a>  COleException::m_sc  
 Ce membre de données contient le code d’état OLE qui indique la raison de l’exception.  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>Notes  
 Valeur de cette variable est définie par [AfxThrowOleException](exception-processing.md#afxthrowoleexception).  
  
 Pour plus d’informations sur `SCODE`, consultez [Structure of COM Error Codes](http://msdn.microsoft.com/library/windows/desktop/ms690088) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="process"></a>  COleException::Process  
 Appelez le **processus** fonction membre pour convertir une exception interceptée dans un code d’état OLE.  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>Paramètres  
 *pAnyException*  
 Pointeur vers une exception interceptée.  
  
### <a name="return-value"></a>Valeur de retour  
 Un code d’état OLE.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette fonction est **statique**.  
  
 Pour plus d’informations sur `SCODE`, consultez [Structure of COM Error Codes](http://msdn.microsoft.com/library/windows/desktop/ms690088) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CALCDRIV](../../visual-cpp-samples.md)   
 [CException (classe)](../../mfc/reference/cexception-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



