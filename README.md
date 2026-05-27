resource "azurerm_resource_group" "ram" {
 name     = "ram"
  location = "West Europe"
}

*********************************************

resource "azurerm_resource_group" "ram" {
   count = 5
  name     = "ram-${count.index}"
 location = "West Europe"
}


********************************************

variable "rg" {
 default = ["ram", "shjyam", "ghanshyam"]
}

resource "azurerm_resource_group" "rg" {
 count    = length(var.rg)
  name     = "rg-${var.rg[count.index]}"
  location = "Central India"
}


variable "rg" {
 default = ["ram", "shjyam", "ghanshyam"]
}
variable "location" {
default = ["eastus", "centralus", "westus2"]
}

resource "azurerm_resource_group" "rg" {
 count    = length(var.rg)
  name     = "rg-${var.rg[count.index]}"
  location = var.location[count.index]
}


resource "azurerm_resource_group" "ram" {
    for_each = toset(["ram","shyam","ramu"])
    name = each.value
    location = "eastus"
  
}
