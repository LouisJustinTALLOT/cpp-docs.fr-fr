---
description: 'En savoir plus sur : classe codecvt_base'
title: codecvt_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: d0fb5a56a163ba80cee89eb6f37200243e6c08e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325099"
---
# <a name="codecvt_base-class"></a>codecvt_base, classe

Classe de base pour la classe codecvt utilisée pour définir un type énumération appelé `result` , utilisé comme type de retour pour les fonctions membres de facette pour indiquer le résultat d’une conversion.

## <a name="syntax"></a>Syntaxe

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>Notes

La classe décrit une énumération commune à toutes les spécialisations du modèle de classe [codecvt](../standard-library/codecvt-class.md). Le résultat de l’énumération décrit les valeurs de retour possibles de [do_in](../standard-library/codecvt-class.md#do_in) ou [do_out](../standard-library/codecvt-class.md#do_out) :

- `ok` Si la conversion entre les encodages de caractères internes et externes est réussie.

- `partial` Si la destination n’est pas assez grande pour que la conversion aboutisse.

- `error` Si la séquence source est incorrecte.

- `noconv` si la fonction n’exécute aucune conversion.

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
