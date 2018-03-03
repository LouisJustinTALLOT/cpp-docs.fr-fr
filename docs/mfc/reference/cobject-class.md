---
title: CObject (classe) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
dev_langs:
- C++
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0384392d42196e4365c59670537819435ce1e45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cobject-class"></a>CObject (classe)
Classe de base principale pour la bibliothèque MFC (Microsoft Foundation Class).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CObject::CObject](#cobject)|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CObject::AssertValid](#assertvalid)|Valide l’intégrité de l’objet.|  
|[CObject::Dump](#dump)|Génère un vidage de diagnostic de cet objet.|  
|[CObject::GetRuntimeClass](#getruntimeclass)|Retourne le `CRuntimeClass` structure correspondant à cette classe de l’objet.|  
|[CObject::IsKindOf](#iskindof)|Teste la relation de cet objet dans une classe donnée.|  
|[CObject::IsSerializable](#isserializable)|Vérifie si cet objet peut être sérialisé.|  
|[CObject::Serialize](#serialize)|Charge ou stocke un objet à partir de dans une archive.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Suppression de CObject::operator](#operator_delete)|Spécial **supprimer** opérateur.|  
|[CObject::operator nouveau](#operator_new)|Spécial **nouveau** opérateur.|  
  
## <a name="remarks"></a>Notes  
 Elle sert de racine non seulement pour les classes de bibliothèque, tel que `CFile` et `CObList`, mais également pour les classes que vous écrivez. `CObject`Fournit des services de base, y compris  
  
-   Prise en charge de la sérialisation  
  
-   Informations de classe d’exécution  
  
-   Sortie de diagnostic d’objet  
  
-   Compatibilité avec les classes de collection  
  
 Notez que `CObject` ne prend pas en charge l’héritage multiple. Vos classes dérivées peuvent avoir qu’un seul `CObject` classe de base et `CObject` doit être à l’extrême gauche dans la hiérarchie. Il est possible, toutefois, pour que les structures et non- `CObject`-classes dérivées de droite branches d’héritage multiple.  
  
 Vous bénéficiez des avantages principaux avantages de `CObject` si vous utilisez des macros facultatif dans votre implémentation de la classe et les déclarations de dérivation.  
  
 Les macros de premier niveau, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) et [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), autoriser l’accès d’exécution pour le nom de classe et de sa position dans la hiérarchie. Cette opération, permet à son tour, le vidage de diagnostic significatifs.  
  
 Les macros de second niveau, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), inclure toutes les fonctionnalités des macros de premier niveau, et ils permettent à un objet « sérialisation » vers et à partir d’une « archive ».  
  
 Pour plus d’informations sur la dérivation de Microsoft Foundation classes et des classes C++ en général et à l’aide de `CObject`, consultez [à l’aide de CObject](../../mfc/using-cobject.md) et [sérialisation](../../mfc/serialization-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CObject`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
  
##  <a name="assertvalid"></a>CObject::AssertValid  
 Valide l’intégrité de l’objet.  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>Notes  
 `AssertValid`effectue une vérification de validité sur cet objet en vérifiant son état interne. Dans la version Debug de la bibliothèque, `AssertValid` peut déclarer et donc fin avec un message qui répertorie le numéro de ligne et le nom de fichier où l’assertion a échoué.  
  
 Lorsque vous écrivez votre propre classe, vous devez substituer la `AssertValid` fonction pour fournir des services de diagnostic pour vous-même et d’autres utilisateurs de votre classe. Le substituée `AssertValid` appelle généralement la `AssertValid` fonction de sa classe de base avant de rechercher des membres de données uniques à la classe dérivée.  
  
 Étant donné que `AssertValid` est un **const** (fonction), vous ne pouvez pas modifier l’état de l’objet pendant le test. Votre propre classe dérivée `AssertValid` fonctions ne doivent pas lever d’exceptions mais plutôt doit déclarer si ils détectent les données d’objet non valide.  
  
 La définition de « validité » dépend de la classe de l’objet. En règle générale, la fonction doit effectuer une « vérification partielle ». Autrement dit, si un objet contient des pointeurs vers les autres objets, il doit vérifier si les pointeurs ne sont pas null, mais il ne doit pas exécuter des tests sur les objets référencés par les pointeurs de validité.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 Pour un autre exemple, consultez [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).  
  
##  <a name="cobject"></a>CObject::CObject  
 Ces fonctions sont la norme `CObject` constructeurs.  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 *objectSrc*  
 Une référence à un autre`CObject`  
  
### <a name="remarks"></a>Notes  
 La version par défaut est automatiquement appelée par le constructeur de votre classe dérivée.  
  
 Si votre classe est sérialisable (il intègre le `IMPLEMENT_SERIAL` (macro)), doit disposer d’un constructeur par défaut (un constructeur sans arguments) dans votre déclaration de classe. Si vous n’avez pas besoin d’un constructeur par défaut, déclarez privée ou protégée constructeur « vide ». Pour plus d’informations, consultez [à l’aide de CObject](../../mfc/using-cobject.md).  
  
 Le constructeur de copie de classe C++ par défaut standard effectue une copie membre-par-membre. La présence de privé `CObject` constructeur de copie garantit un message d’erreur du compilateur si le constructeur de copie de votre classe est requise mais non disponible. Vous devez donc fournir un constructeur de copie si votre classe requiert cette fonctionnalité.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans le `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>CObject::Dump  
 Vide le contenu de l’objet pour un [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objet.  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `dc`  
 Le contexte de dump de diagnostic pour le vidage, généralement `afxDump`.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous écrivez votre propre classe, vous devez substituer la `Dump` fonction pour fournir des services de diagnostic pour vous-même et d’autres utilisateurs de votre classe. Le substituée `Dump` appelle généralement la `Dump` fonction de sa classe de base avant d’imprimer des membres de données uniques à la classe dérivée. `CObject::Dump`Imprime le nom de classe si votre classe utilise le `IMPLEMENT_DYNAMIC` ou `IMPLEMENT_SERIAL` (macro).  
  
> [!NOTE]
>  Votre `Dump` fonction ne doit pas s’imprimer un caractère de saut de ligne à la fin de sa sortie.  
  
 `Dump`appels de sens seulement dans la version Debug de la bibliothèque Microsoft Foundation Class. Vous devez crochet appels, les déclarations de fonction et les implémentations de fonction avec **#ifdef _DEBUG** /  `#endif` instructions de compilation conditionnelle.  
  
 Étant donné que `Dump` est un **const** (fonction), vous ne pouvez pas modifier l’état de l’objet pendant le vidage.  
  
 Le [CDumpContext insertion (<<) opérateur](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) appelle `Dump` lorsqu’un `CObject` pointeur est inséré.  
  
 `Dump`permet le vidage uniquement « acycliques » d’objets. Vous pouvez faire un dump une liste d’objets, par exemple, mais si l’un des objets est la liste elle-même, vous serez finalement dépassement de la pile.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>CObject::GetRuntimeClass  
 Retourne le `CRuntimeClass` structure correspondant à cette classe de l’objet.  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure correspondant à cette classe de l’objet ; jamais **NULL**.  
  
### <a name="remarks"></a>Notes  
 Il y a un `CRuntimeClass` structure pour chaque `CObject`-classe dérivée. Les membres de structure sont les suivantes :  
  
- **LPCSTR m_lpszClassName** une chaîne terminée par le caractère null qui contient le nom de classe ASCII.  
  
- **int m_nObjectSize** la taille de l’objet, en octets. Si l’objet possède des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.  
  
- **UINT m_wSchema** le numéro de schéma (-1 pour les classes non sérialisable). Consultez le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro pour obtenir une description du numéro de schéma.  
  
- **CObject\* (PASCAL\* m_pfnCreateObject) ()** un pointeur de fonction au constructeur par défaut qui crée un objet de votre classe (valide uniquement si la classe prend en charge la création dynamique ; sinon, retourne **NULL** ).  
  
- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** si votre application est dynamiquement liée à la version d’AFXDLL de MFC, un pointeur vers une fonction qui retourne le `CRuntimeClass` structure de la classe de base.  
  
- **CRuntimeClass\* m_pBaseClass** si votre application est liée de manière statique aux MFC, un pointeur vers le `CRuntimeClass` structure de la classe de base.  
  
 Cette fonction nécessite l’utilisation de la [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), ou [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans l’implémentation de classe. Vous obtiendrez des résultats incorrects dans le cas contraire.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>CObject::IsKindOf  
 Teste la relation de cet objet dans une classe donnée.  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `pClass`  
 Un pointeur vers un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure associée à votre `CObject`-classe dérivée.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet correspond à la classe ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction teste `pClass` si (1) il s’agit d’un objet de la classe spécifiée ou (2) il s’agit d’un objet d’une classe dérivée de la classe spécifiée. Cette fonction fonctionne uniquement pour les classes déclarées avec le [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate), ou [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) (macro).  
  
 N’utilisez pas cette fonction largement car elle occulte la fonctionnalité de polymorphisme C++. Utilisez à la place des fonctions virtuelles.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>CObject::IsSerializable  
 Teste si cet objet est éligible pour la sérialisation.  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si cet objet peut être sérialisé ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Pour une classe soit sérialisable, sa déclaration doit contenir le [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) (macro) et l’implémentation doivent contenir le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) (macro).  
  
> [!NOTE]
>  Ne substituez pas cette fonction.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>Suppression de CObject::operator  
 Pour la version de la bibliothèque, opérateur **supprimer** libère la mémoire allouée par l’opérateur **nouveau**.  
  
```  
void PASCAL operator delete(void* p);

 
void PASCAL operator delete(
    void* p,
    void* pPlace);

 
void PASCAL operator delete(
    void* p,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>Notes  
 Dans la version Debug, opérateur **supprimer** fait partie d’un schéma d’analyse de répartition conçu pour détecter les fuites de mémoire.  
  
 Si vous utilisez la ligne de code  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 avant tout dans vos implémentations d’un. CPP de fichiers, puis la troisième version de **supprimer** sera utilisé, le stockage du nom de fichier et numéro de ligne dans le bloc alloué pour le rapport ultérieurement. Vous n’avez pas à vous soucier en fournissant les paramètres supplémentaires ; une macro s’occupe de cela pour vous.  
  
 Même si vous n’utilisez pas `DEBUG_NEW` en mode débogage, vous obtenez encore détection des fuites, mais sans le numéro de ligne de fichier source reporting décrites ci-dessus.  
  
 Si vous remplacez les opérateurs **nouveau** et **supprimer**, perd de cette fonctionnalité de diagnostic.  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans le `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>CObject::operator nouveau  
 Pour la version de la bibliothèque, opérateur **nouveau** effectue une répartition optimale de la mémoire de façon similaire à `malloc`.  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>Notes  
 Dans la version Debug, opérateur **nouveau** fait partie d’un schéma d’analyse de répartition conçu pour détecter les fuites de mémoire.  
  
 Si vous utilisez la ligne de code  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 avant tout dans vos implémentations d’un. CPP de fichiers, puis la deuxième version de **nouveau** sera utilisé, le stockage du nom de fichier et numéro de ligne dans le bloc alloué pour le rapport ultérieurement. Vous n’avez pas à vous soucier en fournissant les paramètres supplémentaires ; une macro s’occupe de cela pour vous.  
  
 Même si vous n’utilisez pas `DEBUG_NEW` en mode débogage, vous obtenez encore détection des fuites, mais sans le numéro de ligne de fichier source reporting décrites ci-dessus.  
  
> [!NOTE]
>  Si vous remplacez cet opérateur, vous devez également substituer **supprimer**. N’utilisez pas la bibliothèque standard **_new_handler** (fonction).  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans le `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>CObject::Serialize  
 Lit ou écrit cet objet dans une archive.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 `ar`  
 A `CArchive` objet à sérialiser vers ou depuis.  
  
### <a name="remarks"></a>Notes  
 Vous devez substituer `Serialize` pour chaque classe que vous souhaitez sérialiser. Le substituée `Serialize` doit d’abord appeler la `Serialize` fonction de sa classe de base.  
  
 Vous devez également utiliser le [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro dans votre déclaration de classe et vous devez utiliser le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans l’implémentation.  
  
 Utilisez [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) ou [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) pour déterminer si l’archive est le chargement ou le stockage.  
  
 `Serialize`est appelée par [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) et [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Ces fonctions sont associées les `CArchive` opérateur d’insertion (  **< \<** ) et l’opérateur d’extraction (  **>>** ).  
  
 Pour des exemples de sérialisation, consultez l’article [sérialisation : sérialisation d’un objet](../../mfc/serialization-serializing-an-object.md).  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



