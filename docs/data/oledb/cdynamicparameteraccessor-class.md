---
title: CDynamicParameterAccessor, classe | Documents Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b9478a5b2cc2190219ce2b297d1908683577c9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097612"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor (classe)

Semblable à [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) mais Obtient des informations sur les paramètres à définir en appelant le [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interface.

## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|Constructeur.|
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|Récupère les données du paramètre en mémoire tampon.|
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|Récupère le nombre de paramètres dans l’accesseur.|
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|Détermine si le paramètre spécifié est un paramètre d’entrée ou de sortie.|
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|Récupère la longueur du paramètre spécifié stocké en mémoire tampon.|
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|Récupère le nom d’un paramètre spécifique.|
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|Récupère l’état du paramètre spécifié stocké en mémoire tampon.|
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|Récupère les données de chaîne du paramètre spécifié stocké en mémoire tampon.|
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|Récupère le type de données d’un paramètre spécifique.|
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|Définit la mémoire tampon à l’aide des données de paramètre.|
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|Définit la longueur du paramètre spécifié stocké en mémoire tampon.|
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|Définit l’état du paramètre spécifié stocké en mémoire tampon.|
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|Définit les données de chaîne du paramètre spécifié stocké en mémoire tampon.|

## <a name="remarks"></a>Notes

Le fournisseur doit prendre en charge `ICommandWithParameters` pour permettre au consommateur d’utiliser cette classe.

Les informations sur les paramètres sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenez les données de paramètre à partir de la mémoire tampon via [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) et [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Pour obtenir un exemple montrant comment utiliser cette classe pour exécuter une procédure stockée SQL Server et d’obtenir les valeurs de paramètre de sortie, consultez le [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) exemple de code dans le [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) référentiel sur GitHub.

## <a name="requirements"></a>Spécifications

**En-tête**: atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor, classe](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)  
