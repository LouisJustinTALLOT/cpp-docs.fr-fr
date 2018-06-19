---
title: CLongBinary (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs:
- C++
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7030fdcb59166c0e70a7b2c2471273c913fe459
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368018"
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
|[CLongBinary::m_hData](#m_hdata)|Contient un Windows `HGLOBAL` handle vers l’objet de l’image réelle.|  
  
## <a name="remarks"></a>Notes  
 Par exemple, un champ d’enregistrement dans une table SQL peut contenir une image bitmap représentant une image. A `CLongBinary` objet stocke un tel objet et effectue le suivi de sa taille.  
  
> [!NOTE]
>  En général, il est maintenant de meilleure pratique d’utiliser [CByteArray](../../mfc/reference/cbytearray-class.md) conjointement avec la [DFX_Binary](record-field-exchange-functions.md#dfx_binary) (fonction). Vous pouvez toujours utiliser `CLongBinary`, mais en général `CByteArray` fournit davantage de fonctionnalités sous Win32, car il n’est plus la limite de taille rencontrée avec 16 bits `CByteArray`. Cet avis s’applique à la programmation avec des objets d’accès aux données (DAO) ainsi que la connectivité ODBC (Open Database).  
  
 Pour utiliser un `CLongBinary` objet, déclarez un membre de données de champ de type `CLongBinary` dans votre classe de recordset. Ce membre sera un membre incorporé de la classe de recordset et est construit avec l’ensemble d’enregistrements est construit. Après le `CLongBinary` objet est construit, le mécanisme de record field exchange (RFX) charge de l’objet de données à partir d’un champ dans l’enregistrement actif sur la source de données et la stocke à l’enregistrement lors de l’enregistrement est mis à jour. RFX interroge la source de données pour la taille de l’objet BLOB, pour qu’il alloue du stockage (via la `CLongBinary` l’objet `m_hData` membre de données) et stocke une `HGLOBAL` handle vers les données de `m_hData`. RFX stocke également la taille réelle de l’objet de données dans le `m_dwDataLength` membre de données. Utiliser les données dans l’objet via `m_hData`, utilisant les mêmes techniques que vous utiliseriez normalement pour manipuler les données stockées dans un Windows `HGLOBAL` gérer.  
  
 Lorsque vous détruisez votre jeu d’enregistrements, incorporé `CLongBinary` également détruit et le destructeur libère le `HGLOBAL` données handle.  
  
 Pour plus d’informations sur les objets de grande taille et l’utilisation de `CLongBinary`, consultez les articles [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) et [Recordset : utilisation avec les éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
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
 Stocke la taille réelle en octets des données stockées dans le `HGLOBAL` gérer dans `m_hData`.  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>Notes  
 Cette taille peut être inférieure à la taille du bloc de mémoire allouée pour les données. Appelez Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593) fonction permettant d’obtenir la taille allouée.  
  
##  <a name="m_hdata"></a>  CLongBinary::m_hData  
 Stocke un Windows `HGLOBAL` handle vers les données d’objet BLOB réel.  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CRecordset, classe](../../mfc/reference/crecordset-class.md)
