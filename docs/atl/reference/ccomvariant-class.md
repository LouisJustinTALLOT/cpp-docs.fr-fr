---
title: Classe de CComVariant | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2ebef74f6da48d2124d69f002a85c467db73406
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366014"
---
# <a name="ccomvariant-class"></a>Classe de CComVariant
Cette classe encapsule le `VARIANT` type, en fournissant un membre indiquant le type de données stockées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
cpp
class CComVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComVariant::CComVariant](#ccomvariant)|Constructeur.|  
|[CComVariant :: ~ CComVariant](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComVariant::Attach](#attach)|Attache un **VARIANT** à la `CComVariant` objet.|  
|[CComVariant::ChangeType](#changetype)|Convertit le `CComVariant` objet à un nouveau type.|  
|[CComVariant::Clear](#clear)|Efface le `CComVariant` objet.|  
|[CComVariant::Copy](#copy)|Copie un **VARIANT** à la `CComVariant` objet.|  
|[CComVariant::CopyTo](#copyto)|Copie le contenu de la `CComVariant` objet.|  
|[CComVariant::Detach](#detach)|Détache sous-jacent **VARIANT** à partir de la `CComVariant` objet.|  
|[CComVariant::GetSize](#getsize)|Retourne la taille en octets du contenu de la `CComVariant` objet.|  
|[CComVariant::ReadFromStream](#readfromstream)|Charge un **VARIANT** à partir d’un flux de données.|  
|[CComVariant::SetByRef](#setbyref)|Initialise le `CComVariant` objet et définit le **vt** membre à **VT_BYREF**.|  
|[CComVariant::WriteToStream](#writetostream)|Enregistre l’objet sous-jacent **VARIANT** dans un flux.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|||  
|-|-|  
|[CComVariant::operator <](#operator_lt)|Indique si le `CComVariant` objet est inférieur à spécifié **variante**.|  
|[CComVariant::operator >](#operator_gt)|Indique si le `CComVariant` objet est supérieur à spécifié **variante**.|  
|[opérateur ! =](#operator_neq)|Indique si le `CComVariant` objet n’est pas égale spécifié **variante**.|  
|[opérateur =](#operator_eq)|Affecte une valeur à la `CComVariant` objet.|  
|[opérateur ==](#operator_eq_eq)|Indique si le `CComVariant` objet est égal à spécifié **variante**.|  
  
## <a name="remarks"></a>Notes  
 `CComVariant` encapsule la `VARIANT and VARIANTARG` type, qui se compose d’une union et d’un membre qui indique le type des données stockées dans l’union. **VARIANT**s sont généralement utilisés dans Automation.  
  
 `CComVariant` dérive de la **VARIANT** tapez afin qu’il peut être utilisé partout où un **VARIANT** peut être utilisé. Vous pouvez, par exemple, utiliser le **V_VT** macro pour extraire le type d’un `CComVariant` ou vous pouvez accéder à la **vt** membre directement comme vous le feriez avec un **VARIANT**.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcomcli.h  
  
##  <a name="attach"></a>  CComVariant::Attach  
 En toute sécurité efface le contenu actuel de la `CComVariant` d’objet, copie le contenu de `pSrc` dans cet objet, puis définit le type variant de `pSrc` à `VT_EMPTY`.  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 `pSrc`  
 [in] Pointe vers le [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) être attaché à l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 La propriété des données détenues par `pSrc` est transféré vers le `CComVariant` objet.  
  
##  <a name="ccomvariant"></a>  CComVariant::CComVariant  
 Chaque constructeur traite l’initialisation sans échec de la `CComVariant` objet en appelant le `VariantInit` fonction Win32 ou en définissant la valeur de l’objet et le type en fonction des paramètres passés.  
  
```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 *varSrc*  
 [in] Le `CComVariant` ou `VARIANT` utilisée pour initialiser le `CComVariant` objet. Le contenu de la variante source est copié vers la destination sans conversion.  
  
 `lpszSrc`  
 [in] La chaîne de caractères utilisée pour initialiser le `CComVariant` objet. Vous pouvez passer une terminant par zéro large (Unicode) chaîne de caractères à la **LPCOLESTR** version du constructeur ou d’une chaîne ANSI pour le `LPCSTR` version. Dans les deux cas, la chaîne est convertie en Unicode `BSTR` allouée à l’aide **SysAllocString**. Le type de la `CComVariant` objet sera `VT_BSTR`.  
  
 `bSrc`  
 [in] Le `bool` utilisée pour initialiser le `CComVariant` objet. Le `bool` argument est converti en un **VARIANT_BOOL** avant d’être stockées. Le type de la `CComVariant` objet sera `VT_BOOL`.  
  
 `nSrc`  
 [in] Le `int`, **octets**, **court**, **long**, **LONGLONG**, **ULONGLONG**, **court non signé**, `unsigned long`, ou `unsigned int` utilisée pour initialiser le `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, ou **VT_UI4**, respectivement.  
  
 `vtSrc`  
 [in] Le type du variant. Lorsque le premier paramètre est `int`, les types valides sont `VT_I4` et **VT_INT**. Lorsque le premier paramètre est **long**, les types valides sont `VT_I4` et `VT_ERROR`. Lorsque le premier paramètre est **double**, les types valides sont `VT_R8` et `VT_DATE`. Lorsque le premier paramètre est `unsigned int`, les types valides sont **VT_UI4** et **VT_UINT**.  
  
 `fltSrc`  
 [in] Le **float** utilisée pour initialiser le `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_R4`.  
  
 `dblSrc`  
 [in] Le **double** utilisée pour initialiser le `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_R8`.  
  
 `cySrc`  
 [in] Le **CY** utilisée pour initialiser le `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_CY`.  
  
 `pSrc`  
 [in] Le `IDispatch` ou **IUnknown** pointeur utilisé pour initialiser le `CComVariant` objet. `AddRef` sera appelée sur le pointeur d’interface. Le type de la `CComVariant` objet sera **VT_DISPATCH** ou **VT_UNKNOWN**, respectivement.  
  
 Sinon, le **SAFERRAY** pointeur utilisé pour initialiser le `CComVariant` objet. Une copie de la **SAFEARRAY** est stocké dans le `CComVariant` objet. Le type de la `CComVariant` objet sera une combinaison du type d’origine de la **SAFEARRAY** et **VT_ARRAY**.  
  
 `cSrc`  
 [in] Le `char` utilisée pour initialiser le `CComVariant` objet. Le type de la `CComVariant` objet sera **VT_I1**.  
  
 `bstrSrc`  
 [in] Le BSTR est utilisé pour initialiser le `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_BSTR`.  
  
### <a name="remarks"></a>Notes  
 Le destructeur gère le nettoyage en appelant [CComVariant::Clear](#clear).  
  
##  <a name="dtor"></a>  CComVariant :: ~ CComVariant  
 Destructeur.  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode gère le nettoyage en appelant [CComVariant::Clear](#clear).  
  
##  <a name="changetype"></a>  CComVariant::ChangeType  
 Convertit le `CComVariant` objet à un nouveau type.  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `vtNew`  
 [in] Le nouveau type de la `CComVariant` objet.  
  
 `pSrc`  
 [in] Un pointeur vers le `VARIANT` dont la valeur sera convertie dans le nouveau type. La valeur par défaut est **NULL**, ce qui signifie que le `CComVariant` objet sera converti en place.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Si vous passez une valeur `pSrc`, `ChangeType` utilisera ce **VARIANT** comme source pour la conversion. Dans le cas contraire, le `CComVariant` objet sera la source.  
  
##  <a name="clear"></a>  CComVariant::Clear  
 Efface le `CComVariant` objet en appelant le `VariantClear` fonction Win32.  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Le destructeur appelle automatiquement **clair**.  
  
##  <a name="copy"></a>  CComVariant::Copy  
 Libère le `CComVariant` de l’objet et lui affecte une copie de l’objet **variante**.  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Paramètres  
 `pSrc`  
 [in] Un pointeur vers le [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) à copier.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="copyto"></a>  CComVariant::CopyTo  
 Copie le contenu de la `CComVariant` objet.  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>Paramètres  
 *pstrDest*  
 Pointe vers un `BSTR` qui recevront une copie du contenu de la `CComVariant` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Le **CComVariant** objet doit être de type `VT_BSTR`.  
  
##  <a name="detach"></a>  CComVariant::Detach  
 Détache sous-jacent **VARIANT** à partir de la `CComVariant` de l’objet et définit le type d’objet `VT_EMPTY`.  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDest`  
 [out] Retourne l’objet sous-jacent `VARIANT` valeur de l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Notez que le contenu de la `VARIANT` référencé par `pDest` sera automatiquement effacé avant d’être assigné à la valeur et le type de l’appel **CComVariant** objet.  
  
##  <a name="getsize"></a>  CComVariant::GetSize  
 Pour une taille fixe de simple `VARIANT`, cette méthode retourne le `sizeof` le type de données sous-jacent plus `sizeof(VARTYPE)`.  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille en octets du contenu actuel de la `CComVariant` objet.  
  
### <a name="remarks"></a>Notes  
 Si le `VARIANT` contient un pointeur d’interface, `GetSize` interroge les `IPersistStream` ou `IPersistStreamInit`. Si succès, la valeur de retour est les 32 bits de poids faible de la valeur retournée par `GetSizeMax` ainsi que les `sizeof` un `CLSID` et `sizeof(VARTYPE)`. Si le pointeur d’interface est `NULL`, `GetSize` retourne le `sizeof` un `CLSID` plus `sizeof(VARTYPE)`. Si la taille totale dépasse `ULONG_MAX`, `GetSize` retourne `sizeof(VARTYPE)` qui indique une erreur.  
  
 Dans tous les autres cas, une valeur temporaire `VARIANT` de type `VT_BSTR` est convertie à partir du `VARIANT`. La longueur de cet `BSTR` est calculée comme la taille de la longueur de la chaîne et la longueur de la chaîne et de la taille du caractère null plu `sizeof(VARTYPE)`. Si le `VARIANT` ne peut pas être converti en un `VARIANT` de type `VT_BSTR`, `GetSize` retourne `sizeof(VARTYPE)`.  
  
 La taille retournée par cette méthode correspond au nombre d’octets utilisés par [CComVariant::WriteToStream](#writetostream) dans des conditions de réussite.  
  
##  <a name="operator_eq"></a>  CComVariant::operator =  
 Affecte une valeur et le type correspondant à la `CComVariant` objet.  
  
```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *varSrc*  
 [in] Le `CComVariant` ou [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) à affecter à la `CComVariant` objet. Le contenu de la variante source est copié vers la destination sans conversion.  
  
 `bstrSrc`  
 [in] Le BSTR à affecter à la `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_BSTR`.  
  
 `lpszSrc`  
 [in] La chaîne de caractères à affecter à la `CComVariant` objet. Vous pouvez passer une terminant par zéro large (Unicode) chaîne de caractères à la **LPCOLESTR** version de l’opérateur ou une chaîne ANSI pour le `LPCSTR` version. Dans les deux cas, la chaîne est convertie en Unicode `BSTR` allouée à l’aide **SysAllocString**. Le type de la `CComVariant` objet sera `VT_BSTR`.  
  
 `bSrc`  
 [in] Le `bool` à affecter à la `CComVariant` objet. Le `bool` argument est converti en un **VARIANT_BOOL** avant d’être stockées. Le type de la `CComVariant` objet sera `VT_BOOL`.  
  
 `nSrc`  
 [in] Le `int`, **octets**, **court**, **long**, **LONGLONG**, **ULONGLONG**, **court non signé**, `unsigned long`, ou `unsigned int` à affecter à la `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, ou **VT_UI4**, respectivement.  
  
 `fltSrc`  
 [in] Le **float** à affecter à la `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_R4`.  
  
 `dblSrc`  
 [in] Le **double** à affecter à la `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_R8`.  
  
 `cySrc`  
 [in] Le **CY** à affecter à la `CComVariant` objet. Le type de la `CComVariant` objet sera `VT_CY`.  
  
 `pSrc`  
 [in] Le `IDispatch` ou **IUnknown** pointeur à affecter à la `CComVariant` objet. `AddRef` sera appelée sur le pointeur d’interface. Le type de la `CComVariant` objet sera **VT_DISPATCH** ou **VT_UNKNOWN**, respectivement.  
  
 Ou, un **SAFEARRAY** pointeur à affecter à la `CComVariant` objet. Une copie de la **SAFEARRAY** est stocké dans le `CComVariant` objet. Le type de la `CComVariant` objet sera une combinaison du type d’origine de la **SAFEARRAY** et **VT_ARRAY**.  
  
 `cSrc`  
 [in] Le caractère à assigner à la `CComVariant` objet. Le type de la `CComVariant` objet sera **VT_I1**.  
  
##  <a name="operator_eq_eq"></a>  CComVariant::operator ==  
 Indique si le `CComVariant` objet est égal à spécifié **variante**.  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne **true** si la valeur et le type de *varSrc* sont égaux à la valeur et le type, respectivement, de la `CComVariant` objet. dans le cas contraire, **false**. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.  
  
 L’opérateur compare uniquement la valeur des types variants. Il compare les chaînes, entiers et virgules flottantes, mais pas les tableaux ou enregistrements.  
  
##  <a name="operator_neq"></a>  CComVariant::operator ! =  
 Indique si le `CComVariant` objet n’est pas égale spécifié **variante**.  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne **true** si la valeur ou un type de *varSrc* n’est pas égal à la valeur ou tapez, respectivement, de la `CComVariant` objet. dans le cas contraire, **false**. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.  
  
 L’opérateur compare uniquement la valeur des types variants. Il compare les chaînes, entiers et virgules flottantes, mais pas les tableaux ou enregistrements.  
  
##  <a name="operator_lt"></a>  CComVariant::operator &lt;  
 Indique si le `CComVariant` objet est inférieur à spécifié **variante**.  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne **true** si la valeur de la `CComVariant` objet est inférieur à la valeur de *varSrc*. dans le cas contraire, **false**. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.  
  
##  <a name="operator_gt"></a>  CComVariant::operator &gt;  
 Indique si le `CComVariant` objet est supérieur à spécifié **variante**.  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne **true** si la valeur de la `CComVariant` objet est supérieur à la valeur de *varSrc*. dans le cas contraire, **false**. L’opérateur utilise les paramètres régionaux par défaut de l’utilisateur pour effectuer la comparaison.  
  
##  <a name="readfromstream"></a>  CComVariant::ReadFromStream  
 Définit l’objet sous-jacent **VARIANT** à la **VARIANT** contenus dans le flux spécifié.  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStream`  
 [in] Un pointeur vers le [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interface sur le flux de données contenant les données.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 **ReadToStream** nécessite un appel précédent à [WriteToStream](#writetostream).  
  
##  <a name="setbyref"></a>  CComVariant::SetByRef  
 Initialise le `CComVariant` objet et définit le **vt** membre à **VT_BYREF**.  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de **VARIANT**, par exemple, `BSTR`, `int`, ou `char`.  
  
 *pT*  
 Le pointeur utilisé pour initialiser le `CComVariant` objet.  
  
### <a name="remarks"></a>Notes  
 `SetByRef` est un modèle de fonction qui initialise le `CComVariant` objet avec le pointeur *pT* et définit les **vt** membre **VT_BYREF**. Par exemple :  
  
 [!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>  CComVariant::WriteToStream  
 Enregistre l’objet sous-jacent **VARIANT** dans un flux.  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Paramètres  
 `pStream`  
 [in] Un pointeur vers le [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interface sur un flux de données.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)