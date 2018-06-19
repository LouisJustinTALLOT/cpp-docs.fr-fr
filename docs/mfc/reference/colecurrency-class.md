---
title: COleCurrency, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
dev_langs:
- C++
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b8139047f47a1984dca9faba3ebff6b0426bb444
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376432"
---
# <a name="colecurrency-class"></a>COleCurrency, classe
Encapsule le type de données `CURRENCY` d'OLE automation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleCurrency  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleCurrency::COleCurrency](#colecurrency)|Construit un objet `COleCurrency`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleCurrency::Format](#format)|Génère une représentation sous forme de chaîne mise en forme d’un `COleCurrency` objet.|  
|[COleCurrency::GetStatus](#getstatus)|Obtient l’état (validité) de ce `COleCurrency` objet.|  
|[COleCurrency::ParseCurrency](#parsecurrency)|Lit un **devise** valeur à partir d’une chaîne et définit la valeur de `COleCurrency`.|  
|[COleCurrency::SetCurrency](#setcurrency)|Définit la valeur de cet `COleCurrency` objet.|  
|[COleCurrency::SetStatus](#setstatus)|Définit l’état (validité) de ce `COleCurrency` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[opérateur =](#operator_eq)|Copie un `COleCurrency` valeur.|  
|[opérateur +, -](#operator_plus_minus)|Ajoute, soustrait et changement de signe de `COleCurrency` valeurs.|  
|[+= (opérateur)-=](#operator_plus_minus_eq)|Ajoute et soustrait un `COleCurrency` valeur à partir de ce `COleCurrency` objet.|  
|[opérateur * /](#operator_star)|Échelles un `COleCurrency` valeur d’une valeur entière.|  
|[opérateur * =, / =](#operator_star_div_eq)|Cela met à l’échelle `COleCurrency` valeur d’une valeur entière.|  
|[opérateur <<](#operator_stream)|Sorties un `COleCurrency` valeur `CArchive` ou `CDumpContext`.|  
|[opérateur >>](#operator_stream)|Entrées une `COleCurrency` à partir de l’objet `CArchive`.|  
|[opérateur de devise](#operator_currency)|Convertit un `COleCurrency` valeur dans un **devise**.|  
|[opérateur ==, <, < =, etc..](#colecurrency_relational_operators)|Compare deux `COleCurrency` valeurs.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|Contient l’objet sous-jacent **devise** pour ce `COleCurrency` objet.|  
|[COleCurrency::m_status](#m_status)|Contient l’état de ce `COleCurrency` objet.|  
  
## <a name="remarks"></a>Notes  
 **COleCurrency** ne dispose pas d’une classe de base.  
  
 **DEVISE** est implémenté en tant que de 8 octets, valeur d’entier de complément à deux multiplié par 10 000. Ceci fournit un nombre à virgule fixe avec 15 chiffres à gauche du séparateur décimal et 4 chiffres à droite. Le **devise** type de données est très utile pour les calculs impliquant des valeurs monétaires, ou pour les calculs à virgule fixe où la précision est importante. C’est un des types possibles pour le `VARIANT` type de données d’OLE automation.  
  
 **COleCurrency** implémente également certaines opérations arithmétiques de base pour ce type à virgule fixe. Les opérations prises en charge ont été sélectionnées pour contrôler les erreurs d’arrondi qui se produisent lors des calculs à virgule fixe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `COleCurrency`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  
  
##  <a name="colecurrency"></a>  COleCurrency::COleCurrency  
 Construit un **COleCurrency** objet.  
  
```  
COleCurrency();  
COleCurrency(CURRENCY cySrc);  
  COleCurrency(const COleCurrency& curSrc);  
COleCurrency(const VARIANT& varSrc);

 
COleCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Paramètres  
 `cySrc`  
 A **devise** valeur à copier dans le nouvel **COleCurrency** objet.  
  
 `curSrc`  
 Existant **COleCurrency** à copier dans le nouvel objet **COleCurrency** objet.  
  
 *varSrc*  
 Existant **VARIANT** structure de données (éventuellement un `COleVariant` objet) à convertir en une valeur monétaire ( `VT_CY`) et le copier dans le nouvel **COleCurrency** objet.  
  
 `nUnits`, `nFractionalUnits`  
 Indiquer les unités et les fractions de seconde partie (de 1/10, 000's) de la valeur à copier dans le nouveau **COleCurrency** objet.  
  
### <a name="remarks"></a>Notes  
 Toutes ces constructeurs créent de nouveaux **COleCurrency** objet initialisé à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit. Sauf indication contraire, l’état de la nouvelle **COleCurrency** élément a la valeur de valide.  
  
- Constructions de COleCurrency() un **COleCurrency** objet initialisé à 0 (zéro).  
  
- COleCurrency (`cySrc`) construit une **COleCurrency** de l’objet d’un [devise](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) valeur.  
  
- COleCurrency (`curSrc`) construit une **COleCurrency** objet d’un existant **COleCurrency** objet. Le nouvel objet a le même état que l’objet source.  
  
- COleCurrency (`varSrc`) construit une **COleCurrency** objet. Tente de convertir un [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) structure ou `COleVariant` objet à une devise ( `VT_CY`) valeur. Si cette conversion réussit, la valeur convertie est copiée dans le nouvel **COleCurrency** objet. Si elle n’est pas le cas, la valeur de la **COleCurrency** objet a la valeur zéro (0) et son état non valide.  
  
- `COleCurrency(`nUnits`, `'nFractionalUnits) construit une **COleCurrency** objet à partir des composants numériques spécifiés. Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué pour les unités. Notez que les unités et la partie fractionnaire sont spécifiées par les valeurs de type long signés.  
  
 Pour plus d’informations, consultez la [devise](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) et [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) entrées dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 Les exemples suivants montrent les effets des constructeurs zéro-paramètre et les deux paramètres :  
  
 [!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="format"></a>  COleCurrency::Format  
 Appelez cette fonction membre pour créer une représentation sous forme de mise en forme de la valeur de devise.  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Indique les indicateurs pour les paramètres régionaux. Seul l’indicateur suivant s’applique à devise :  
  
- **LOCALE_NOUSEROVERRIDE** utiliser des paramètres régionaux par défaut du système, au lieu des paramètres utilisateur personnalisés.  
  
 `lcid`  
 Indique l’ID de paramètres régionaux à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient la valeur de format de devise.  
  
### <a name="remarks"></a>Notes  
 Il met en forme la valeur avec les spécifications de langue locale (ID de paramètres régionaux). Un symbole de devise n’est pas inclus dans la valeur retournée. Si l’état de ce **COleCurrency** objet est null, la valeur de retour est une chaîne vide. Si l’état n’est pas valide, la chaîne de retour est spécifiée par la ressource de chaîne **IDS_INVALID_CURRENCY**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="getstatus"></a>  COleCurrency::GetStatus  
 Appelez cette fonction membre pour obtenir l’état (validité) d’une donnée **COleCurrency** objet.  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’état de ce **COleCurrency** valeur.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour est définie par le `CurrencyStatus` type énuméré qui est défini dans le **COleCurrency** classe.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
- **COleCurrency::valid** indique que cette **COleCurrency** objet est valide.  
  
- **COleCurrency::invalid** indique que cette **COleCurrency** objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
  
- **COleCurrency::null** indique que cette **COleCurrency** objet est null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « null » dans le sens de la base de données de « aucune valeur, les clauses having » plutôt que de C++ **NULL**.)  
  
 L’état d’un **COleCurrency** objet n’est pas valide dans les cas suivants :  
  
-   Si sa valeur est définie à partir d’un **VARIANT** ou `COleVariant` valeur qui n’a pas pu être converti en une valeur monétaire.  
  
-   Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, par exemple `+=` ou **\* =**.  
  
-   Si une valeur non valide a été assignée à cet objet.  
  
-   Si l’état de cet objet a été explicitement défini non valide à l’aide de [SetStatus](#setstatus).  
  
 Pour plus d’informations sur les opérations qui peuvent définir l’état non valide, consultez les fonctions membres suivantes :  
  
- [COleCurrency](#colecurrency)  
  
- [opérateur =](#operator_eq)  
  
- [opérateur + -](#operator_plus_minus)  
  
- [opérateur += et =](#operator_plus_minus_eq)  
  
- [opérateur * /](#operator_star)  
  
- [opérateur * = et / =](#operator_star_div_eq)  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]  
  
##  <a name="m_cur"></a>  COleCurrency::m_cur  
 Sous-jacent [devise](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) structure pour ce **COleCurrency** objet.  
  
### <a name="remarks"></a>Notes  
  
> [!CAUTION]
>  Modification de la valeur dans la **devise** structure accédé par le pointeur retourné par cette fonction modifie la valeur de ce **COleCurrency** objet. Il ne modifie pas l’état de ce **COleCurrency** objet.  
  
 Pour plus d’informations, consultez la [devise](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) entrée dans le SDK Windows.  
  
##  <a name="m_status"></a>  COleCurrency::m_status  
 Le type de ce membre de données est le type énuméré `CurrencyStatus`, qui est défini dans le **COleCurrency** classe.  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>Notes  
 Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
- **COleCurrency::valid** indique que cette **COleCurrency** objet est valide.  
  
- **COleCurrency::invalid** indique que cette **COleCurrency** objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
  
- **COleCurrency::null** indique que cette **COleCurrency** objet est null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « null » dans le sens de la base de données de « aucune valeur, les clauses having » plutôt que de C++ **NULL**.)  
  
 L’état d’un **COleCurrency** objet n’est pas valide dans les cas suivants :  
  
-   Si sa valeur est définie à partir d’un **VARIANT** ou `COleVariant` valeur qui n’a pas pu être converti en une valeur monétaire.  
  
-   Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, par exemple `+=` ou **\* =**.  
  
-   Si une valeur non valide a été assignée à cet objet.  
  
-   Si l’état de cet objet a été explicitement défini non valide à l’aide de [SetStatus](#setstatus).  
  
 Pour plus d’informations sur les opérations qui peuvent définir l’état non valide, consultez les fonctions membres suivantes :  
  
- [COleCurrency](#colecurrency)  
  
- [opérateur =](#operator_eq)  
  
- [opérateur +, -](#operator_plus_minus)  
  
- [+= (opérateur)-=](#operator_plus_minus_eq)  
  
- [opérateur * /](#operator_star)  
  
- [opérateur * =, / =](#operator_star_div_eq)  
  
    > [!CAUTION]
    >  Ce membre de données concerne les situations de programmation avancées. Vous devez utiliser les fonctions de membre inline [GetStatus](#getstatus) et [SetStatus](#setstatus). Consultez `SetStatus` pour les autres avertissements concernant la définition explicite de ce membre de données.  
  
##  <a name="operator_eq"></a>  COleCurrency::operator =  
 Ces opérateurs d’assignation surchargés copiez la valeur de devise source dans cette **COleCurrency** objet.  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>Notes  
 Une brève description de chaque opérateur suit :  
  
- **opérateur = (** `cySrc` **)** le `CURRENCY` valeur est copiée dans le **COleCurrency** objet et son état est défini à valide.  
  
- **opérateur = (** `curSrc` **)** la valeur et l’état de l’opérande existant **COleCurrency** objet sont copiés dans ce **COleCurrency** objet .  
  
- **opérateur = (** *varSrc* **)** si la conversion de la `VARIANT` valeur (ou [COleVariant](../../mfc/reference/colevariant-class.md) objet) à une devise ( `VT_CY`) est réussite, la valeur convertie est copiée dans ce **COleCurrency** objet et son état est défini à valide. Si la conversion n’est pas réussie, la valeur de la **COleCurrency** objet est défini à 0 et son état non valide.  
  
 Pour plus d’informations, consultez la [devise](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) et [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) entrées dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="operator_plus_minus"></a>  COleCurrency::operator +, -  
 Ces opérateurs permettent d’ajouter ou soustraire deux **COleCurrency** valeurs vers et à partir de l’autre et pour modifier le signe d’un **COleCurrency** valeur.  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>Notes  
 Si une des opérandes est null, l’état de la **COleCurrency** la valeur est null.  
  
 Si l’opération arithmétique dépasse, résultant **COleCurrency** valeur n’est pas valide.  
  
 Si l’opérande n’est pas valide et l’autre n’est ne pas null, l’état de la **COleCurrency** valeur n’est pas valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="operator_plus_minus_eq"></a>  COleCurrency::operator +=-=  
 Vous permettent d’ajouter ou soustraire un **COleCurrency** valeur vers et à partir de ce **COleCurrency** objet.  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>Notes  
 Si une des opérandes est null, l’état de ce **COleCurrency** objet est défini avec la valeur null.  
  
 Si l’opération arithmétique dépasse, l’état de ce **COleCurrency** objet est défini à non valide.  
  
 Si un des opérandes n’est pas valide et que l’autre n’est pas null, l’état de ce **COleCurrency** objet est défini à non valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="operator_star"></a>  COleCurrency::operator * et /  
 Vous permettent de faire évoluer un **COleCurrency** valeur par une valeur intégrale.  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>Notes  
 Si le **COleCurrency** des opérandes est null, l’état de la **COleCurrency** la valeur est null.  
  
 Si l’opération arithmétique dépasse positifs et négatifs, l’état de la **COleCurrency** valeur n’est pas valide.  
  
 Si le **COleCurrency** opérande n’est pas valide, l’état de la **COleCurrency** valeur n’est pas valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="operator_star_div_eq"></a>  COleCurrency::operator * =, / =  
 Vous permettent de faire évoluer ce **COleCurrency** valeur par une valeur intégrale.  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>Notes  
 Si le **COleCurrency** des opérandes est null, l’état de ce **COleCurrency** objet est défini avec la valeur null.  
  
 Si l’opération arithmétique dépasse, l’état de ce **COleCurrency** objet est défini à non valide.  
  
 Si le **COleCurrency** opérande n’est pas valide, l’état de ce **COleCurrency** objet est défini à non valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="operator_stream"></a>  COleCurrency::operator &lt; &lt;, &gt;&gt;  
 Prend en charge les vidages de diagnostic et de stockage dans une archive.  
  
```  
friend CDumpContext& operator<<(
    CDumpContext& dc,  
    COleCurrency curSrc);
 
friend CArchive& operator<<(
    CArchive& ar,  
    COleCurrency curSrc);
 
friend CArchive& operator>>(
    CArchive& ar,  
    COleCurrency& curSrc);
```  
  
### <a name="remarks"></a>Notes  
 L’extraction ( **>>**) (opérateur) prend en charge le chargement à partir d’une archive.  
  
##  <a name="operator_currency"></a>  COleCurrency::operator devise  
 Retourne un `CURRENCY` structure dont la valeur est copiée à partir de ce **COleCurrency** objet.  
  
```  
operator CURRENCY() const; 
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="parsecurrency"></a>  COleCurrency::ParseCurrency  
 Appelez cette fonction membre pour analyser une chaîne pour lire une valeur monétaire.  
  
```  
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,  
    DWORD dwFlags = 0,  
    LCID lcid = LANG_USER_DEFAULT);
 
throw(CMemoryException*); 
throw(COleException*);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszCurrency*  
 Pointeur vers la chaîne se terminant par null qui doit être analysé.  
  
 `dwFlags`  
 Indique les indicateurs pour les paramètres régionaux, éventuellement l’indicateur suivant :  
  
- **LOCALE_NOUSEROVERRIDE** utiliser des paramètres régionaux par défaut du système, au lieu des paramètres utilisateur personnalisés.  
  
 `lcid`  
 Indique l’ID de paramètres régionaux à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la chaîne a été correctement convertie en une valeur monétaire, sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Il utilise des spécifications de langue locale (ID de paramètres régionaux) pour la signification des caractères non numériques dans la chaîne source.  
  
 Pour une présentation des valeurs d’ID de paramètres régionaux, consultez [prenant en charge plusieurs langues](http://msdn.microsoft.com/en-us/47dc5add-232c-4268-b977-43e12da81ede).  
  
 Si la chaîne a été correctement convertie en une devise de valeur, la valeur de cet **COleCurrency** objet est défini pour cette valeur et son état valide.  
  
 Si la chaîne n’a pas pu être convertie en une valeur monétaire ou s’il existe un dépassement de capacité numérique, l’état de ce **COleCurrency** objet n’est pas valide.  
  
 Si la conversion de chaîne a échoué en raison d’erreurs d’allocation de mémoire, cette fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md). Dans n’importe quel autre état d’erreur, cette fonction lève un [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="colecurrency_relational_operators"></a>  Opérateurs relationnels COleCurrency  
 Comparer deux valeurs de devise et de retour différente de zéro si la condition est true ; Sinon, 0.  
  
```  
BOOL operator==(const COleCurrency& cur) const;  
BOOL operator!=(const COleCurrency& cur) const;  
BOOL operator<(const COleCurrency& cur) const;  
BOOL operator>(const COleCurrency& cur) const;  
BOOL operator<=(const COleCurrency& cur) const;  
BOOL operator>=(const COleCurrency& cur) const;  
```  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  La valeur de retour des opérations de tri ( **<**, **\< =**, **>**, **>=**) n’est pas défini si l’état de des opérandes est null ou non valide. Les opérateurs d’égalité ( `==`, `!=`) envisagez de l’état des opérandes.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="setcurrency"></a>  COleCurrency::SetCurrency  
 Appelez cette fonction membre pour définir les unités et les fractions de seconde partie de cette **COleCurrency** objet.  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Paramètres  
 `nUnits`, `nFractionalUnits`  
 Indiquer les unités et les fractions de seconde partie (de 1/10, 000's) de la valeur à copier dans cette **COleCurrency** objet.  
  
### <a name="remarks"></a>Notes  
 Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué pour les unités, comme indiqué dans la troisième des exemples suivants.  
  
 Notez que les unités et la partie fractionnaire sont spécifiées par les valeurs de type long signés. La quatrième des exemples suivants illustre ce qui se passe lorsque les paramètres ont des signes différents.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="setstatus"></a>  COleCurrency::SetStatus  
 Appelez cette fonction membre pour définir l’état (validité) de ce **COleCurrency** objet.  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>Paramètres  
 *status*  
 Le nouvel état pour ce **COleCurrency** objet.  
  
### <a name="remarks"></a>Notes  
 Le *état* la valeur du paramètre est définie par le `CurrencyStatus` type énuméré, qui est défini dans le **COleCurrency** classe.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
- **COleCurrency::valid** indique que cette **COleCurrency** objet est valide.  
  
- **COleCurrency::invalid** indique que cette **COleCurrency** objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
  
- **COleCurrency::null** indique que cette **COleCurrency** objet est null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (Il s’agit de « null » dans le sens de la base de données de « aucune valeur, les clauses having » plutôt que de C++ **NULL**.)  
  
    > [!CAUTION]
    >  Cette fonction concerne les situations de programmation avancées. Cette fonction ne modifie pas les données dans cet objet. Il est plus souvent être utilisé pour définir l’état null ou non valide. Notez que l’opérateur d’assignation ( [opérateur =](#operator_eq)) et [SetCurrency](#setcurrency) ne définissez pas l’état de l’objet basé sur les valeurs de la source.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleVariant, classe](../../mfc/reference/colevariant-class.md)
