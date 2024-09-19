object pepita {
  var energy = 100

  method energy() = energy

  method fly(minutes) {
    energy = energy - minutes * 3
  }
}

object gandalf {

  var vida = 0
  const armas = #{baculo, espada}

  method armas() { return armas }

  method vida(_vida) {
    vida = (_vida).max(0).min(100)
  }

  method poder() = if (vida > 10) vida*15 + self.sumatoriaDelPoderDeSusArmas()*2 
  else vida*300 + self.sumatoriaDelPoderDeSusArmas()*2

  method sumatoriaDelPoderDeSusArmas() = armas.sum({arma => arma.poderDelArma()})

  method puedePasar(zona) = zona.cumpleCondicion(self)
}

object baculo {
  const poder = 400

  method poderDelArma() = poder
}

object espada {
  var origen = elfico
  var poder = 0

  method origen(_origen) {
    origen = _origen
  }

  method poderDelArma() { 
  poder = origen.poderOrigen()*10
  return poder
}
}

object elfico {
  const poderOrigen = 25

  method poderOrigen() = poderOrigen
}

object enano {
  const poderOrigen = 20

  method poderOrigen() = poderOrigen
}

object humano {
  const poderOrigen = 15

  method poderOrigen() = poderOrigen
}

object lebennin {

  method cumpleCondicion(individuo) = individuo.poder() > 1500
}

object minasTirith {

  method cumpleCondicion(individuo) = not(individuo.armas().isEmpty())
}
