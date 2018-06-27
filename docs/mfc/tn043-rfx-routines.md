---
title: 'TN043 : Routines RFX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RFX
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc6556cabaa8f1f04a2a53771b495233620e1a14
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954407"
---
# <a name="tn043-rfx-routines"></a>TN043 : routines RFX
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit l’architecture d’exchange (RFX) des champs d’enregistrements. Elle décrit également la façon dont vous écrivez un **RFX_** procédure.  
  
## <a name="overview-of-record-field-exchange"></a>Vue d’ensemble de l’échange de champs d’enregistrement  
 Toutes les fonctions de champ de recordset sont effectuées avec le code C++. Il n’existe aucune des ressources particulières ou des macros magiques. Le cœur du mécanisme est une fonction virtuelle qui doit être substituée dans chaque classe dérivée de jeu d’enregistrements. Il existe toujours dans cet écran :  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{ *//{{AFX_FIELD_MAP(CMySet)  
 <recordset exchange field type call>  
 <recordset exchange function call> *//}}AFX_FIELD_MAP  
}  
```  
  
 Les commentaires AFX format spécial autoriser ClassWizard localiser et modifier le code dans cette fonction. Code qui n’est pas compatible avec ClassWizard doit être placé en dehors de commentaires spéciaux de format.  
  
 Dans l’exemple ci-dessus, < recordset_exchange_field_type_call > se présente sous la forme :  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);
```  
  
 et < recordset_exchange_function_call > se présente sous la forme :  
  
```  
RFX_Custom(pFX, "Col2",
    m_Col2);
```  
  
 La plupart des **RFX_** fonctions ont trois arguments, comme indiqué ci-dessus, mais certains (par exemple, `RFX_Text` et `RFX_Binary`) ont des arguments facultatifs supplémentaires.  
  
 Plusieurs **RFX_** peut être inclus dans chaque `DoDataExchange` (fonction).  
  
 Consultez « afxdb.h » pour obtenir la liste de toutes les routines d’échange de champ de recordset fournis avec MFC.  
  
 Appels de champ de Recordset sont un moyen de l’inscription des emplacements de mémoire (généralement les membres de données) pour stocker les données de champ pour un `CMySet` classe.  
  
## <a name="notes"></a>Notes  
 Fonctions de champ de Recordset sont conçues pour fonctionner uniquement avec la `CRecordset` classes. Ils ne sont plus généralement utilisables par d’autres classes MFC.  
  
 Les valeurs initiales des données sont définies dans le constructeur C++ standard, généralement dans un bloc avec `//{{AFX_FIELD_INIT(CMylSet)` et `//}}AFX_FIELD_INIT` commentaires.  
  
 Chaque **RFX_** fonction doit prendre en charge diverses opérations, qu’il s’agisse de retourner l’état de non-intégrité du champ à l’archivage du champ de préparation pour la modification du champ.  
  
 Chaque fonction qui appelle `DoFieldExchange` (par exemple `SetFieldNull`, `IsFieldDirty`), est son propre initialisation autour de l’appel à `DoFieldExchange`.  
  
## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il  
 Vous n’avez pas besoin de comprendre les éléments suivants pour pouvoir utiliser l’échange de champs d’enregistrements. Toutefois, comprendre comment cela fonctionne en arrière-plan vous aideront à écrire votre propre procédure exchange.  
  
 Le `DoFieldExchange` fonction membre est très semblable à la `Serialize` fonction membre, il est responsable de l’obtention ou la définition des données vers/depuis un formulaire externe (dans ce cas colonnes à partir du résultat d’une requête ODBC) à partir de/vers des données membres dans la classe. Le *pFX* paramètre constitue le contexte de l’opération d’échange de données et est semblable à la *CArchive* paramètre `CObject::Serialize`. Le *pFX* (un `CFieldExchange` objet) a un indicateur d’opération, qui est similaire à, mais une généralisation de le *CArchive* indicateur de direction. Fonctions RFX peut-être prendre en charge les opérations suivantes :  
  
- `BindParam` : Indiquer où ODBC doit récupérer les données de paramètre  
  
- `BindFieldToColumn` : Indiquer où ODBC doit récupérer/dépôt outputColumn données  
  
- `Fixup` : Définissez `CString/CByteArray` longueurs, définir le statut de valeur NULL de bits  
  
- `MarkForAddNew` — Marque incorrectes si la valeur a changé depuis l’appel de AddNew  
  
- `MarkForUpdate` — Marque incorrectes si la valeur a changé depuis l’appel de l’édition  
  
- `Name` Ajouter des noms de champs pour les champs marqués comme modifiés  
  
- `NameValue` : Permet d’ajouter «\<nom de colonne > = » pour les champs marqués comme modifiés  
  
- `Value` : Permet d’ajouter « » suivi d’un séparateur, telles que ',' ou ' '  
  
- `SetFieldDirty` : Définition de champ (c'est-à-dire modifiées) incorrectes bits d’état  
  
- `SetFieldNull` : Définissez le bit d’état indiquant la valeur null pour le champ  
  
- `IsFieldDirty` : Valeur de retour de bit d’état modifié  
  
- `IsFieldNull` : Valeur de retour de bits d’état est null  
  
- `IsFieldNullable` : Renvoie la valeur TRUE si le champ peut contenir des valeurs NULL  
  
- `StoreField` : Valeur de champ d’archivage  
  
- `LoadField` — Recharger la valeur du champ archivés  
  
- `GetFieldInfoValue` : Retourne des informations générales sur un champ  
  
- `GetFieldInfoOrdinal` : Retourne des informations générales sur un champ  
  
## <a name="user-extensions"></a>Extensions de l’utilisateur  
 Il existe plusieurs façons d’étendre le mécanisme RFX par défaut. Vous pouvez  
  
-   Ajouter de nouveaux types de données. Exemple :  
  
 ```  
    CBookmark 
 ```  
  
-   Ajouter de nouvelles procédures exchange (RFX_).  
  
 ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
    const char *szName,  
    BIGINT& value);

 ```  
  
-   Avoir le `DoFieldExchange` fonction membre incluent de manière conditionnelle des appels RFX supplémentaires ou autres instructions C++ valides.  
  
 ```  
    while (posExtraFields != NULL)  
 {  
    RFX_Text(pFX,
    m_listName.GetNext(posExtraFields),   
    m_listValue.GetNext(posExtraValues));

 }  
 ```  
  
> [!NOTE]
>  Ce code ne peut pas être modifié par ClassWizard et doit être utilisé uniquement en dehors de commentaires spéciaux de format.  
  
## <a name="writing-a-custom-rfx"></a>L’écriture d’un RFX personnalisé  
 Pour écrire votre propre fonction personnalisée RFX, il est recommandé que vous copiez une fonction RFX existante et modifiez en fonction de vos besoins. En sélectionnant le droit RFX à copier peut faciliter votre travail. Certaines fonctions RFX ont des propriétés uniques à prendre en compte lorsque vous décidez de laquelle copier.  
  
 `RFX_Long` et `RFX_Int`:  
 Ce sont les fonctions RFX la plus simple. La valeur de données n’a pas besoin toute interprétation spéciale, et la taille des données est fixe.  
  
 `RFX_Single` et `RFX_Double`:  
 Comme RFX_Long et RFX_Int ci-dessus, ces fonctions sont simples et faire utiliser largement de l’implémentation par défaut. Ils sont stockés dans dbflt.cpp au lieu de dbrfx.cpp, toutefois, pour activer le chargement du runtime bibliothèque virgule flottante uniquement lorsqu’elles sont explicitement référence.  
  
 `RFX_Text` et `RFX_Binary`:  
 Ces deux fonctions allouer une mémoire tampon statique pour contenir les informations de type chaîne ou binaire et doivent l’inscrire ces mémoires tampons avec ODBC SQLBindCol au lieu de l’inscription et la valeur. Pour cette raison, ces deux fonctions ont une grande quantité de code spécial.  
  
 `RFX_Date`:  
 ODBC retourne des informations de date et d’heure dans leur propre structure de données TIMESTAMP_STRUCT. Cette fonction alloue dynamiquement un TIMESTAMP_STRUCT en tant que « proxy » pour envoyer et recevoir des données de date du temps. Diverses opérations doivent transférer les informations de date et d’heure entre le C++ `CTime` objet et le proxy TIMESTAMP_STRUCT. Cela complique considérablement cette fonction, mais elle est un bon exemple d’utilisation d’un proxy pour le transfert de données.  
  
 `RFX_LongBinary`:  
 Il s’agit de la bibliothèque de classes uniquement fonction RFX qui n’utilise pas de liaison de colonne pour recevoir et envoyer des données. Cette fonction ignore l’opération BindFieldToColumn au lieu de cela, lors de l’opération de correction, alloue du stockage pour contenir les données SQL_LONGVARCHAR ou SQL_LONGVARBINARY entrantes, puis effectue un appel de SQLGetData pour récupérer la valeur dans le stockage alloué. Lorsque vous préparez renvoyer des valeurs de données à la source de données (telles que les opérations NameValue et valeur), cette fonction utilise la fonctionnalité DATA_AT_EXEC d’ODBC. Consultez [Note technique 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) pour plus d’informations sur l’utilisation de SQL_LONGVARBINARY et SQL_LONGVARCHARs.  
  
 Lorsque vous écrivez votre propre **RFX_** fonction, souvent pouvoir utiliser `CFieldExchange::Default` pour implémenter une opération donnée. Examinez l’implémentation de la valeur par défaut pour l’opération en question. Si elle effectue l’opération vous écririez votre **RFX_** fonction, vous pouvez déléguer à la `CFieldExchange::Default`. Vous pouvez voir des exemples de l’appel de `CFieldExchange::Default` dans dbrfx.cpp  
  
 Il est important d’appeler `IsFieldType` au début de votre fonction RFX, puis revenez immédiatement si elle retourne FALSE. Ce mécanisme conserve le paramètre exécuter les opérations de sur *outputColumns*et vice versa (telle qu’un appel `BindParam` sur une *outputColumn*). En outre, `IsFieldType` automatiquement assure le suivi du nombre de *outputColumns* (*m_nFields*) et params (*m_nParams*).  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

