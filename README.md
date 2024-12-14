# OE-4

class Character:
    def __init__(self, name, health, power):
        self.name = name
        self.health = health
        self.power = power

    def attack(self, target):
        target.health -= self.power
        print(f"{self.name} attacks⚔️  {target.name}! {target.name} HP: {target.health}♡♡♡")

    def special_move(self, target):
        pass
    
    def defend(self, attacker):
        reduced_damage = max(0, attacker.power - 50)
        self.health -= reduced_damage
        print(f"{self.name} defends🛡 {self.name}'s HP: {self.health}")


class Warrior(Character):
    def special_move(self, target):
        print(f"Warrior {self.name} uses Shield Bash🛡  {target.name}!")
        self.power *= 2
        self.attack(target)


class Mage(Character):
    def special_move(self, target):
        print(f"Mage {self.name} casts Fireball🔥  {target.name}!")
        target.health -= 100
        print(f"{target.name} takes 100 damage! {target.name} has {target.health} HP l.")


class Archer(Character):
    def special_move(self, target):
        print(f"Archer {self.name} shoots a Piercing Arrow🏹  {target.name}!")
        target.health -= self.power
        print(f"{target.name} takes {self.power} damage! {target.name} has {target.health} HP left.")


class Monster(Character):
    def __init__(self, name, health, power, heal_amount):
        super().__init__(name, health, power)
        self.heal_amount = heal_amount

    def special_move(self, target):
        print(f"Monster {self.name} roars and attacks {target.name}!")
        self.attack(target)
        self.health += self.heal_amount
        print(f"Monster {self.name} heals for {self.heal_amount} HP. {self.name} now has {self.health} HP.")

warrior = Warrior("Cyrus", 1000, 150)
mage = Mage("Lisa", 700, 200)
archer = Archer("Tighnari", 800, 120)
monster = Monster("Raiden Shogun", 900, 80, 50)

for character in (warrior, mage, archer):
    character.special_move(monster)

for character in (warrior, mage, archer):
    monster.special_move(character)
