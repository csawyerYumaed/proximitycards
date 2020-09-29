# proximitycards
ProximityCards algorithm for converting between diff formats.

There are known to me 2 different forms of numbers for proximity cards. There are online calculators like: https://btrockford.com/security/card-access-control/proximity-card-calculator/  But all the explanations that talk about how this works are not very practical.

This is the practical conversion, to let you move on with life, in Python:

```python
def dec_to_prox(d):
	'''
	to convert decimal #(serialized number) to the number on the
	proximity card. Returns a value in the form 999,99999
	'''
	h = '{:X}'.format(d)
	n1 = int(h[:2], 16)
	n2 = int(h[2:-4], 16)
	return '{},{}'.format(n1, n2)


def prox_to_dec(p):
	'''
	given a proximity card of the form 999,99999 this returns
	the decimal number(serialized card number).  The numbers
	are converted to hex {:X} and then concatenated to 101A.
	the first 3 hex are the Facility Code and the last set after the comma is the Card Number
	'''
	n1, n2 = p.split(',')
	return int('{:X}{:04X}101A'.format(int(n1), int(n2)), 16)
  ```



Hope this helps.

Converts a facility code formatted number to full or serialized card number
For use with 125KHz Wiegand 26 Bit ISO Cards and Tags
