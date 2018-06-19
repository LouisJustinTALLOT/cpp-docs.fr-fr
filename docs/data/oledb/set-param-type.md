---
title: SET_PARAM_TYPE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SET_PARAM_TYPE
dev_langs:
- C++
helpviewer_keywords:
- SET_PARAM_TYPE macro
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ab4884032425f13c2cc506d6e66c955eb439f7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107413"
---
# <a name="setparamtype"></a>SET_PARAM_TYPE
Spécifie les macros `COLUMN_ENTRY` qui suivent l’entrée, la sortie ou l’entrée/sortie de macro `SET_PARAM_TYPE` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
SET_PARAM_TYPE(type)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `type`  
 [in] Type à définir pour le paramètre.  
  
## <a name="remarks"></a>Notes  
 Les fournisseurs prennent en charge uniquement les types d’entrée/sortie de paramètres qui sont pris en charge par la source de données sous-jacente. Le type est une combinaison d’une ou plusieurs valeurs **DBPARAMIO** (voir [Structures DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) dans les *Informations de référence du programmeur OLE DB*) :  
  
-   **DBPARAMIO_NOTPARAM** L’accesseur n’a aucun paramètre. En général, vous affectez cette valeur à **eParamIO** dans les accesseurs de ligne pour rappeler à l’utilisateur que les paramètres sont ignorés.  
  
-   **DBPARAMIO_INPUT** Paramètre d’entrée.  
  
-   **DBPARAMIO_OUTPUT** Paramètre de sortie.  
  
-   **DBPARAMIO_INPUT &#124; DBPARAMIO_OUTPUT** le paramètre est une entrée et un paramètre de sortie.  
  
## <a name="example"></a>Exemple  
```
cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)