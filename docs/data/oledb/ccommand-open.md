---
title: CCommand::Open | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 82b87ad01bf072358042e9af7170afea1f7d4e88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092087"
---
# <a name="ccommandopen"></a>CCommand::Open
S’exécute et éventuellement lie la commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `session`  
 [in] La session dans laquelle exécuter la commande.  
  
 `wszCommand`  
 [in] La commande à exécuter, passé comme une chaîne Unicode. Peut être **NULL** lors de l’utilisation `CAccessor`, auquel cas la commande à extraire de la valeur passée à la [DEFINE_COMMAND](../../data/oledb/define-command.md) (macro). Consultez [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) dans les *de référence du programmeur OLE DB* pour plus d’informations.  
  
 `szCommand`  
 [in] Identique à `wszCommand` , sauf que ce paramètre accepte une chaîne de commande ANSI. La quatrième forme de cette méthode peut prendre une valeur NULL. Consultez la section « Remarques » plus loin dans cette rubrique pour plus d’informations.  
  
 *pPropSet*  
 [in] Un pointeur vers un tableau de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) les structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](https://msdn.microsoft.com/en-us/library/ms713696.aspx) dans les *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.  
  
 `pRowsAffected`  
 [entrée/sortie] Pointeur vers la mémoire où le nombre de lignes affectées par une commande est retourné. Si  *\*pRowsAffected* est **NULL**, aucun nombre de lignes n’est retourné. Dans le cas contraire, **ouvrir** définit *`pRowsAffected` selon les conditions suivantes :  
  
|If|Then|  
|--------|----------|  
|Le **cParamSets** élément de `pParams` est supérieur à 1|*`pRowsAffected` représente le nombre total de lignes affectées par tous les jeux de paramètres spécifiés dans l’exécution.|  
|Le nombre de lignes affectées n’est pas disponible|*`pRowsAffected` a la valeur -1.|  
|La commande ne met pas à jour, supprimer ou insérer des lignes|*`pRowsAffected` n’est pas défini.|  
  
 `guidCommand`  
 [in] GUID qui spécifie la syntaxe et les règles générales pour le fournisseur à utiliser dans l’analyse du texte de commande. Consultez [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) et [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) dans les *de référence du programmeur OLE DB* pour plus d’informations.  
  
 `bBind`  
 [in] Spécifie s’il faut lier la commande automatiquement une fois en cours d’exécution. La valeur par défaut est **true**, ce qui entraîne la commande à lier automatiquement. Paramètre `bBind` à **false** empêche la liaison automatique de la commande de sorte que vous pouvez lier manuellement. (Liaison manuelle est particulièrement intéressant pour les utilisateurs OLAP).  
  
 `ulPropSets`  
 [in] Le nombre de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) structures passées dans le *pPropSet* argument.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Les trois premières formes de **ouvrir** prendre une session, créer une commande et exécutez la commande, tous les paramètres de liaison selon les besoins.  
  
 La première forme de **ouvrir** prend une chaîne de commande Unicode et n’a aucune valeur par défaut.  
  
 La deuxième forme de **ouvrir** prend une chaîne de commande ANSI et aucune valeur par défaut (fourni pour la compatibilité descendante avec les applications existantes ANSI).  
  
 La troisième forme de **ouvrir** permet à la chaîne de commande soit NULL, en raison de type `int` avec une valeur par défaut NULL. Il est fourni pour l’appel `Open(session, NULL);` ou `Open(session);` , car la valeur NULL est de type `int`. Cette version requiert et déclare que le `int` paramètre être NULL.  
  
 Le quatrième écran de **ouvrir** lorsque vous avez déjà créé une commande et que vous souhaitez effectuer un seul [préparation](../../data/oledb/ccommand-prepare.md) et plusieurs exécutions.  
  
> [!NOTE]
>  **Ouvrez** appelle **Execute**, qui à son tour appelle `GetNextResult`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CCommand, classe](../../data/oledb/ccommand-class.md)