---
title: COLECurrency, classe | Microsoft Docs
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
ms.openlocfilehash: 1077a9567509d98b68a864d7478ab84b94d11054
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42541639"
---
# <a name="colecurrency-class"></a>COLECurrency, classe
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
|[COleCurrency::ParseCurrency](#parsecurrency)|Lit une valeur monétaire d’une chaîne et définit la valeur de `COleCurrency`.|  
|[COleCurrency::SetCurrency](#setcurrency)|Définit la valeur de cette `COleCurrency` objet.|  
|[COleCurrency::SetStatus](#setstatus)|Définit l’état (validité) pour cet `COleCurrency` objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[opérateur =](#operator_eq)|Copie un `COleCurrency` valeur.|  
|[opérateur +, -](#operator_plus_minus)|Ajoute, soustrait et modifie le signe de `COleCurrency` valeurs.|  
|[opérateur +=, =](#operator_plus_minus_eq)|Ajoute et soustrait un `COleCurrency` valeur à partir de ce `COleCurrency` objet.|  
|[opérateur * /](#operator_star)|Échelles un `COleCurrency` valeur d’une valeur entière.|  
|[opérateur * =, / =](#operator_star_div_eq)|Cela met à l’échelle `COleCurrency` valeur d’une valeur entière.|  
|[opérateur <<](#operator_stream)|Sorties un `COleCurrency` valeur `CArchive` ou `CDumpContext`.|  
|[opérateur >>](#operator_stream)|Entrées un `COleCurrency` à partir de l’objet `CArchive`.|  
|[opérateur de devise](#operator_currency)|Convertit un `COleCurrency` valeur en devise.|  
|[opérateur ==, <, < =, etc..](#colecurrency_relational_operators)|Compare deux `COleCurrency` valeurs.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|Contient la devise sous-jacent pour ce `COleCurrency` objet.|  
|[COleCurrency::m_status](#m_status)|Contient l’état de ce `COleCurrency` objet.|  
  
## <a name="remarks"></a>Notes  
 `COleCurrency` n’a pas d’une classe de base.  
  
 DEVISE est implémentée en tant que de 8 octets, à l’échelle par 10 000 nombre entier de complément à 2. Ceci fournit un nombre à virgule fixe avec 15 chiffres à gauche du séparateur décimal et 4 chiffres à droite. Le type de données de devise est extrêmement utile pour les calculs impliquant des valeurs monétaires, ou pour tout calcul à virgule fixe où la précision est importante. C’est un des types possibles pour le `VARIANT` type de données d’OLE automation.  
  
 `COleCurrency` implémente également certaines opérations arithmétiques de base pour ce type à virgule fixe. Les opérations prises en charge ont été sélectionnées pour contrôler les erreurs d’arrondi qui se produisent lors des calculs à virgule fixe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `COleCurrency`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdisp.h  
  
##  <a name="colecurrency"></a>  COleCurrency::COleCurrency  
 Construit un objet `COleCurrency`.  
  
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
 *cySrc*  
 Valeur monétaire doit être copié dans le nouveau `COleCurrency` objet.  
  
 *curSrc*  
 Un existant `COleCurrency` objet doit être copié dans le nouveau `COleCurrency` objet.  
  
 *varSrc*  
 Un existant `VARIANT` structure de données (éventuellement un `COleVariant` objet) à être convertie en une valeur monétaire (VT_CY) et copiés dans le nouvel `COleCurrency` objet.  
  
 *nUnits*, *nFractionalUnits*  
 Indiquer les unités et les fractions de seconde partie (en 1/10 000 s) de la valeur doit être copié dans le nouveau `COleCurrency` objet.  
  
### <a name="remarks"></a>Notes  
 Toutes ces constructeurs créent `COleCurrency` objets initialisés à la valeur spécifiée. Une brève description de chacun de ces constructeurs suit. Sauf indication contraire, l’état de la nouvelle `COleCurrency` élément est défini à valide.  
  
- Constructions de COleCurrency() un `COleCurrency` objet initialisé à 0 (zéro).  
  
- COleCurrency (`cySrc`) construit un `COleCurrency` de l’objet à partir d’un [devise](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e) valeur.  
  
- COleCurrency (`curSrc`) construit un `COleCurrency` objet depuis une `COleCurrency` objet. Le nouvel objet a le même état que l’objet source.  
  
- COleCurrency (`varSrc`) construit un `COleCurrency` objet. Tente de convertir un [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) structure ou `COleVariant` objet en une valeur monétaire (VT_CY). Si cette conversion est réussie, la valeur convertie est copiée dans le nouvel `COleCurrency` objet. Si elle n’est pas le cas, la valeur de la `COleCurrency` objet est défini sur zéro (0) et son état comme étant non valide.  
  
- `COleCurrency(`nUnits`, `nFractionalUnits`) Constructs a `COleCurrency' objet à partir de composants numériques spécifiés. Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué pour les unités. Notez que les unités et la partie fractionnaire sont spécifiés par les valeurs de type long signés.  
  
 Pour plus d’informations, consultez le [devise](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e) et [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) entrées dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 Les exemples suivants montrent les effets des constructeurs de paramètre de zéro et deux paramètres :  
  
 [!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="format"></a>  COleCurrency::Format  
 Appelez cette fonction membre pour créer une représentation sous forme de mise en forme de la valeur de devise.  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>Paramètres  
 *dwFlags*  
 Indique les indicateurs de paramètres régionaux. Seul l’indicateur suivant est pertinente pour la devise :  
  
- LOCALE_NOUSEROVERRIDE utiliser les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.  
  
 *lcid*  
 Indique l’ID de paramètres régionaux à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` qui contient la valeur monétaire mise en forme.  
  
### <a name="remarks"></a>Notes  
 Il met en forme la valeur en utilisant les spécifications de langue locale (ID de paramètres régionaux). Un symbole monétaire n’est pas inclus dans la valeur retournée. Si l’état de ce `COleCurrency` objet est null, la valeur de retour est une chaîne vide. Si l’état n’est pas valide, la chaîne de retour est spécifiée par la ressource de chaîne IDS_INVALID_CURRENCY.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="getstatus"></a>  COleCurrency::GetStatus  
 Appelez cette fonction membre pour obtenir l’état (validité) d’une donnée `COleCurrency` objet.  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’état de ce `COleCurrency` valeur.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour est définie par le `CurrencyStatus` type énuméré qui est défini dans le `COleCurrency` classe.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
  - `COleCurrency::valid` Indique que ce `COleCurrency` objet est valide.  
  
  - `COleCurrency::invalid` Indique que ce `COleCurrency` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
  
  - `COleCurrency::null` Indique que ce `COleCurrency` objet a la valeur null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « null » dans le sens de la base de données de « ne having aucune valeur, », par opposition à la valeur NULL en C++.)  
  
 L’état d’un `COleCurrency` objet n’est pas valide dans les cas suivants :  
  
-   Si sa valeur est définie à partir d’une variante ou `COleVariant` valeur qui n’a pas pu être converti en une valeur monétaire.  
  
-   Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, par exemple `+=` ou **\* =**.  
  
-   Si une valeur non valide a été affectée à cet objet.  
  
-   Si l’état de cet objet a été explicitement défini sur non valide à l’aide de [SetStatus](#setstatus).  
  
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
 Sous-jacent [devise](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e) structure pour ce `COleCurrency` objet.  
  
### <a name="remarks"></a>Notes  
  
> [!CAUTION]
>  Modification de la valeur dans le `CURRENCY` structure accédé par le pointeur retourné par cette fonction modifie la valeur de ce `COleCurrency` objet. Il ne modifie pas l’état de ce `COleCurrency` objet.  
  
 Pour plus d’informations, consultez le [devise](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e) entrée dans le SDK Windows.  
  
##  <a name="m_status"></a>  COleCurrency::m_status  
 Le type de ce membre de données est le type énuméré `CurrencyStatus`, qui est défini dans le `COleCurrency` classe.  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>Notes  
Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
 - `COleCurrency::valid` Indique que ce `COleCurrency` objet est valide.  
      
 - `COleCurrency::invalid` Indique que ce `COleCurrency` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
      
 - `COleCurrency::null` Indique que ce `COleCurrency` objet a la valeur null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « null » dans le sens de la base de données de « ne having aucune valeur, », par opposition à la valeur NULL en C++.)  
  
L’état d’un `COleCurrency` objet n’est pas valide dans les cas suivants :  
  
 - Si sa valeur est définie à partir d’une variante ou `COleVariant` valeur qui n’a pas pu être converti en une valeur monétaire.  
      
 - Si cet objet a rencontré un dépassement de capacité positif ou négatif pendant une opération arithmétique d’assignation, par exemple `+=` ou **\* =**.  
      
 - Si une valeur non valide a été affectée à cet objet.  
      
 - Si l’état de cet objet a été explicitement défini sur non valide à l’aide de [SetStatus](#setstatus).  
  
Pour plus d’informations sur les opérations qui peuvent définir l’état non valide, consultez les fonctions membres suivantes :  
  
 - [COleCurrency](#colecurrency)  
      
 - [opérateur =](#operator_eq)  
      
 - [opérateur +, -](#operator_plus_minus)  
      
 - [opérateur +=, =](#operator_plus_minus_eq)  
      
 - [opérateur * /](#operator_star)  
      
 - [opérateur * =, / =](#operator_star_div_eq)  
  
> [!CAUTION]
>  Ce membre de données concerne les situations de programmation avancées. Vous devez utiliser les fonctions de membre inline [GetStatus](#getstatus) et [SetStatus](#setstatus). Consultez `SetStatus` pour des précautions supplémentaires concernant la définition explicite de ce membre de données.  
  
##  <a name="operator_eq"></a>  COleCurrency::operator =  
 Ces opérateurs d’assignation surchargés copier la valeur de devise source dans cette `COleCurrency` objet.  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>Notes  
 Une brève description de chaque opérateur suit :  
  
- **opérateur = (** `cySrc` **)** le `CURRENCY` valeur est copiée dans le `COleCurrency` objet et son état est défini à valide.  
  
- **opérateur = (** `curSrc` **)** la valeur et l’état de l’opérande existant `COleCurrency` objet sont copiés dans ce `COleCurrency` objet.  
  
- **opérateur = (** *varSrc* **)** si la conversion de la `VARIANT` valeur (ou [COleVariant](../../mfc/reference/colevariant-class.md) objet) en devise ( `VT_CY`) est réussite, la valeur convertie est copiée dans ce `COleCurrency` objet et son état est défini à valide. Si la conversion n’est pas réussie, la valeur de la `COleCurrency` objet est défini sur 0 et son état comme étant non valide.  
  
 Pour plus d’informations, consultez le [devise](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e) et [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) entrées dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="operator_plus_minus"></a>  COleCurrency::operator +, -  
 Ces opérateurs permettent d’ajouter ou soustraire deux `COleCurrency` valeurs vers et de l’autre et pour modifier le signe d’un `COleCurrency` valeur.  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>Notes  
 Si un des opérandes est null, l’état des résultats de `COleCurrency` la valeur est null.  
  
 Si l’opération arithmétique dépasse, résultant `COleCurrency` valeur n’est pas valide.  
  
 Si l’opérande n’est pas valide et l’autre n’est ne pas null, l’état des résultats de `COleCurrency` valeur n’est pas valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="operator_plus_minus_eq"></a>  COleCurrency::operator +=, =  
 Vous permettent d’ajouter et de soustraire un `COleCurrency` valeur vers et depuis ce `COleCurrency` objet.  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>Notes  
 Si une des opérandes est null, l’état de ce `COleCurrency` objet est défini avec la valeur null.  
  
 Si l’opération arithmétique dépassements de capacité, l’état de ce `COleCurrency` objet est défini comme étant non valide.  
  
 Si un des opérandes n’est pas valide et que l’autre n’est pas null, l’état de ce `COleCurrency` objet est défini comme étant non valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="operator_star"></a>  COleCurrency::operator \* et /  
 Vous permettent de mettre à l’échelle un `COleCurrency` valeur par une valeur intégrale.  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>Notes  
 Si le `COleCurrency` des opérandes est null, l’état des résultats de `COleCurrency` la valeur est null.  
  
 Si l’opération arithmétique dépassements de capacité positifs et négatifs, l’état des résultats de `COleCurrency` valeur n’est pas valide.  
  
 Si le `COleCurrency` opérande n’est pas valide, l’état des résultats de `COleCurrency` valeur n’est pas valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="operator_star_div_eq"></a>  COleCurrency::operator \*=, / =  
 Vous permettent à l’échelle cette `COleCurrency` valeur par une valeur intégrale.  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>Notes  
 Si le `COleCurrency` des opérandes est null, l’état de ce `COleCurrency` objet est défini avec la valeur null.  
  
 Si l’opération arithmétique dépassements de capacité, l’état de ce `COleCurrency` objet est défini comme étant non valide.  
  
 Si le `COleCurrency` opérande n’est pas valide, l’état de ce `COleCurrency` objet est défini comme étant non valide.  
  
 Pour plus d’informations sur les valeurs d’état valide, null et non valides, consultez la [m_status](#m_status) variable membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="operator_stream"></a>  COleCurrency::operator &lt; &lt;, &gt;&gt;  
 Prend en charge le vidage de diagnostic et de stockage dans une archive.  
  
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
 L’extraction ( **>>**) opérateur prend en charge le chargement à partir d’une archive.  
  
##  <a name="operator_currency"></a>  COleCurrency::operator devise  
 Retourne un `CURRENCY` structure dont la valeur est copiée à partir de ce `COleCurrency` objet.  
  
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
  
 *dwFlags*  
 Indique les indicateurs pour les paramètres régionaux, éventuellement l’indicateur suivant :  
  
- LOCALE_NOUSEROVERRIDE utiliser les paramètres régionaux par défaut du système, plutôt que les paramètres utilisateur personnalisés.  
  
 *lcid*  
 Indique l’ID de paramètres régionaux à utiliser pour la conversion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la chaîne a été convertie en une valeur monétaire, sinon 0.  
  
### <a name="remarks"></a>Notes  
 Il utilise les spécifications de langue locale (ID de paramètres régionaux) pour la signification des caractères non numériques dans la chaîne source.  
  
 Pour une description des valeurs d’ID de paramètres régionaux, consultez [prenant en charge plusieurs langues](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).  
  
 Si la chaîne a été correctement convertie en devise valeur, la valeur de ce `COleCurrency` objet est défini sur cette valeur et son état à valide.  
  
 Si la chaîne n’a pas pu être convertie en une valeur monétaire, ou s’il y avait un dépassement de capacité numérique, l’état de ce `COleCurrency` objet n’est pas valide.  
  
 Si la conversion de chaîne a échoué en raison d’erreurs d’allocation de mémoire, cette fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md). Dans n’importe quel autre état d’erreur, cette fonction lève un [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="colecurrency_relational_operators"></a>  Opérateurs relationnels COleCurrency  
 Comparer deux valeurs de devise et de retour différent de zéro si la condition est vraie ; sinon 0.  
  
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
>  La valeur de retour des opérations de tri ( **<**, **\< =**, **>**, **>=**) n’est pas défini si l’état de des opérandes est null ou non valide. Les opérateurs d’égalité ( `==`, `!=`) prendre en compte l’état des opérandes.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="setcurrency"></a>  COleCurrency::SetCurrency  
 Appelez cette fonction membre pour définir les unités et la partie fractionnaire de ce `COleCurrency` objet.  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Paramètres  
 *nUnits*, *nFractionalUnits*  
 Indiquer les unités et les fractions de seconde partie (en 1/10 000 s) de la valeur doit être copié dans ce `COleCurrency` objet.  
  
### <a name="remarks"></a>Notes  
 Si la valeur absolue de la partie fractionnaire est supérieure à 10 000, l’ajustement approprié est effectué pour les unités, comme indiqué dans la troisième des exemples suivants.  
  
 Notez que les unités et la partie fractionnaire sont spécifiés par les valeurs de type long signés. La quatrième des exemples suivants montre que se passe-t-il lorsque les paramètres ont des signes différents.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="setstatus"></a>  COleCurrency::SetStatus  
 Appelez cette fonction membre pour définir l’état (validité) de ce `COleCurrency` objet.  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>Paramètres  
 *status*  
 Le nouvel état pour ce `COleCurrency` objet.  
  
### <a name="remarks"></a>Notes  
 Le *état* valeur du paramètre est définie par le `CurrencyStatus` type énuméré, qui est défini dans le `COleCurrency` classe.  
  
```  
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };  
```  
  
 Pour obtenir une brève description de ces valeurs d’état, consultez la liste suivante :  
  
- `COleCurrency::valid` Indique que ce `COleCurrency` objet est valide.  
  
- `COleCurrency::invalid` Indique que ce `COleCurrency` objet n’est pas valide ; autrement dit, sa valeur peut être incorrecte.  
  
- `COleCurrency::null` Indique que ce `COleCurrency` objet a la valeur null, c'est-à-dire qu’aucune valeur n’a été fournie pour cet objet. (C’est « null » dans le sens de la base de données de « ne having aucune valeur, », par opposition à la valeur NULL en C++.)  
  
> [!CAUTION]
>  Cette fonction concerne les situations de programmation avancées. Cette fonction ne modifie pas les données dans cet objet. Il sera plus souvent être utilisé pour définir l’état non valide ou null. Notez que l’opérateur d’assignation ( [opérateur =](#operator_eq)) et [SetCurrency](#setcurrency) définir l’état de l’objet basé sur la valeur (s) source.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleVariant, classe](../../mfc/reference/colevariant-class.md)
