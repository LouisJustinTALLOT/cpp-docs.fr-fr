---
title: codecvt_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6f957c39f9c78fd182b7ba2a14bdab7f27db56ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405298"
---
# <a name="codecvtbase-class"></a>codecvt_base, classe

Une classe de base pour la classe codecvt qui sert à définir un type d’énumération appelé `result`, utilisé comme type de retour pour les fonctions membres de facette pour indiquer le résultat d’une conversion.

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

Cette classe décrit une énumération commune à toutes les spécialisations de la classe de modèle [codecvt](../standard-library/codecvt-class.md). Le résultat de l’énumération décrit les valeurs de retour possibles de [do_in](../standard-library/codecvt-class.md#do_in) ou [do_out](../standard-library/codecvt-class.md#do_out) :

- `ok` Si la conversion entre les encodages de caractères internes et externes réussit.

- `partial` Si la destination n’est pas assez grande pour que la conversion réussisse.

- `error` Si la séquence source est malade formée.

- `noconv` si la fonction n’exécute aucune conversion.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
