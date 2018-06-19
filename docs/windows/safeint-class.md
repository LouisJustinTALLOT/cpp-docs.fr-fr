---
title: SafeInt, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce7715553e17e49ef3c169145abfb49816f6d6dd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891335"
---
# <a name="safeint-class"></a>SafeInt, classe
Étend les primitives entières afin d’empêcher le dépassement sur les entiers et vous permet de comparer les différents types d’entiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>  
class SafeInt;  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Modèle|Description|  
|--------------|-----------------|  
|T|Le type d’entier ou un paramètre booléen qui `SafeInt` remplace.|  
|E|Type de données énuméré qui définit la stratégie de gestion d’erreur.|  
|U|Type d’entier ou un paramètre booléen pour l’opérande secondaire.|  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] rhs|Un paramètre d’entrée qui représente la valeur située à droite de l’opérateur dans plusieurs fonctions autonomes.|  
|[in] i|Un paramètre d’entrée qui représente la valeur située à droite de l’opérateur dans plusieurs fonctions autonomes.|  
|[in] bits|Un paramètre d’entrée qui représente la valeur située à droite de l’opérateur dans plusieurs fonctions autonomes.|  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|Constructeur par défaut.|  
  
### <a name="assignment-operators"></a>Opérateurs d'assignation  
  
|Name|Syntaxe|  
|----------|------------|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|  
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|  
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|  
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|  
  
### <a name="casting-operators"></a>Opérateurs de casting  
  
|Name|Syntaxe|  
|----------|------------|  
|bool|`operator bool() throw()`|  
|char|`operator char() const`|  
|signed char|`operator signed char() const`|  
|unsigned char|`operator unsigned char() const`|  
|__int16|`operator __int16() const`|  
|unsigned __int16|`operator unsigned __int16() const`|  
|__int32|`operator __int32() const`|  
|unsigned __int32|`operator unsigned __int32() const`|  
|long|`operator long() const`|  
|unsigned long|`operator unsigned long() const`|  
|__int64|`operator __int64() const`|  
|unsigned __int64|`operator unsigned __int64() const`|  
|wchar_t|`operator wchar_t() const`|  
  
### <a name="comparison-operators"></a>Opérateurs de comparaison  
  
|Name|Syntaxe|  
|----------|------------|  
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|  
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|  
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|  
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|  
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|  
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|  
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|  
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|  
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|  
|==|`bool operator== (bool rhs) const throw()`|  
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|  
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|  
|!=|`bool operator!= (bool b) const throw()`|  
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|  
  
### <a name="arithmetic-operators"></a>Opérateurs arithmétiques  
  
|Name|Syntaxe|  
|----------|------------|  
|+|`const SafeInt<T,E>& operator+ () const throw()`|  
|-|`SafeInt<T,E> operator- () const`|  
|++|`SafeInt<T,E>& operator++ ()`|  
|--|`SafeInt<T,E>& operator-- ()`|  
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|  
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|  
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|  
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|  
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|  
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|  
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|  
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|  
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|  
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|  
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|  
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|  
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|  
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|  
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|  
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|  
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|  
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|  
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|  
  
### <a name="logical-operators"></a>Opérateurs logiques  
  
|Name|Syntaxe|  
|----------|------------|  
|!|`bool operator !() const throw()`|  
|~|`SafeInt<T,E> operator~ () const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|  
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|  
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|  
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|  
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|  
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|  
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|  
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|  
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|  
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|  
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|  
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|  
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|  
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|  
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|  
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|  
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|  
  
## <a name="remarks"></a>Notes  
 La `SafeInt` classe protège contre le dépassement sur les entiers dans des opérations mathématiques. Par exemple, envisagez d’ajouter deux entiers 8 bits : un a la valeur 200 et la seconde a la valeur 100. L’opération mathématique correcte serait 200 + 100 = 300. Toutefois, en raison de la limite de 8 bits, le bit supérieur est perdu et le compilateur retourne 44 (300-2<sup>8</sup>) comme résultat. Toute opération qui dépend de cette équation mathématique générera un comportement inattendu.  
  
 La `SafeInt` classe vérifie si un dépassement de capacité arithmétique a lieu ou indique si le code tente de diviser par zéro. Dans les deux cas, la classe appelle le Gestionnaire d’erreurs pour avertir le programme de ce problème.  
  
 Cette classe vous permet également de comparer deux types d’entiers tant qu’ils sont `SafeInt` objets. En règle générale, lorsque vous effectuez une comparaison, vous devez d’abord convertir les nombres pour être du même type. Conversion d’un nombre à un autre type souvent requiert des vérifications pour vous assurer qu’il n’existe aucune perte de données.  
  
 La table des opérateurs dans cette rubrique répertorie les opérateurs mathématiques et de comparaison pris en charge par la `SafeInt` classe. Opérateurs mathématiques plus retournent un `SafeInt` objet de type `T`.  
  
 Opérations de comparaison entre un `SafeInt` et un type intégral peut être effectué dans les deux sens. Par exemple, les deux `SafeInt<int>(x) < y` et `y> SafeInt<int>(x)` sont valides et retourne le même résultat.  
  
 De nombreux opérateurs binaires ne prennent pas en charge l’aide de deux `SafeInt` types. Un exemple est le `&` opérateur. `SafeInt<T, E> & int` est pris en charge, mais `SafeInt<T, E> & SafeInt<U, E>` n’est pas. Dans ce dernier exemple, le compilateur ne sait pas quel type de paramètre à retourner. Une solution à ce problème consiste à convertir le deuxième paramètre vers le type de base. En utilisant les mêmes paramètres, cela peut être fait avec `SafeInt<T, E> & (U)SafeInt<U, E>`.  
  
> [!NOTE]
>  Pour les opérations au niveau du bit, les deux paramètres doivent avoir la même taille. Si les tailles sont différentes, le compilateur génère une [ASSERT](../mfc/reference/diagnostic-services.md#assert) exception. Les résultats de cette opération ne peut pas être garanties exacte. Pour résoudre ce problème, effectuez un cast le plus petit paramètre jusqu'à ce qu’il s’agit de la même taille que le paramètre supérieure.  
  
 Pour les opérateurs de décalage, un décalage de plus de bits qu’existe pour le type de modèle lève une exception de l’assertion. Cela aura aucun effet en mode release. Il est possible pour les opérateurs de décalage de mélange des deux types de paramètres de SafeInt, car le type de retour est le même que le type d’origine. Le nombre situé à droite de l’opérateur n'indique que le nombre de bits à décaler.  
  
 Lorsque vous effectuez une comparaison logique avec un objet SafeInt, la comparaison est strictement arithmétique. Par exemple, considérez ces expressions :  
  
-   `SafeInt<uint>((uint)~0) > -1`  
  
-   `((uint)~0) > -1`  
  
 La première instruction est résolue en `true`, mais la deuxième instruction correspond à `false`. La négation au niveau du bit 0 est 0xFFFFFFFF. Dans la deuxième instruction, l’opérateur de comparaison par défaut compare 0xFFFFFFFF à 0xFFFFFFFF et considère qu’ils soient égaux. L’opérateur de comparaison pour la `SafeInt` classe se rend compte que le second paramètre est négatif, alors que le premier paramètre n’est pas signé. Par conséquent, bien que la représentation sous forme de bits est identique, la `SafeInt` opérateur logique se rend compte que l’entier non signé est supérieure à -1.  
  
 Soyez prudent lorsque vous utilisez la `SafeInt` classe avec le `?:` opérateur ternaire. Envisagez de la ligne de code suivante.  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : -1;  
```  
  
 Le compilateur convertit à ceci :  
  
```  
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);  
```  
  
 Si `flag` est `false`, le compilateur lève une exception au lieu d’affecter la valeur -1 pour `x`. Par conséquent, pour éviter ce comportement, le code correct à utiliser est la ligne suivante.  
  
```  
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;  
```  
  
 `T` et `U` peuvent être affectés à un type booléen, type de caractère ou type entier. L’entier types peuvent être signés ou non signés et n’importe quelle taille de 8 bits à 64 bits.  
  
> [!NOTE]
>  Bien que la `SafeInt` classe accepte tout type d’entier, il effectue plus efficacement avec les types non signés.  
  
 `E` est le mécanisme de gestion des erreurs qui `SafeInt` utilise. Deux mécanismes de gestion des erreurs sont fournis avec la Bibliothèque SafeInt. La stratégie par défaut est `SafeIntErrorPolicy_SafeIntException`, qui lève une [SafeIntException, classe](../windows/safeintexception-class.md) exception lorsqu’une erreur se produit. L’autre stratégie est `SafeIntErrorPolicy_InvalidParameter`, ce qui arrête le programme si une erreur se produit.  
  
 Il existe deux options pour personnaliser la stratégie de l’erreur. La première option consiste à définir le paramètre `E` lorsque vous créez un `SafeInt`. Utilisez cette option lorsque vous souhaitez modifier les erreurs de gestion de stratégie pour un seul `SafeInt`. L’autre option consiste à définir `_SAFEINT_DEFAULT_ERROR_POLICY` à votre classe de gestion des erreurs personnalisée avant d’inclure le `SafeInt` bibliothèque. Utilisez cette option lorsque vous souhaitez modifier l’erreur par défaut la gestion des stratégies pour toutes les instances de la `SafeInt` classe dans votre code.  
  
> [!NOTE]
>  Une classe personnalisée qui gère les erreurs de la Bibliothèque SafeInt ne doit pas retourner de contrôle au code qui a appelé le Gestionnaire d’erreurs. Une fois que le Gestionnaire d’erreurs est appelée, le résultat de la `SafeInt` opération ne peut pas être approuvée.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** safeint.h  
  
 **Namespace :** msl::utilities  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeIntException Class](../windows/safeintexception-class.md)