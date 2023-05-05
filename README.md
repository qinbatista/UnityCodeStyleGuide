# Overview
```CSharp

public class GameManager : Singleton<GameManager>
{
    [SerializeField] Transform _landTransform;
    [SerializeField] bool _isPlayerWalking;
    public event Action<int> EventPointsScored;
    public Transform LandTransform { get => _landTransform; }
    
	// the private backing field
    private int maxHealth;
    // read-only, returns backing field
    public int MaxHealth => maxHealth;
    // equivalent to:
    // public int MaxHealth { get; private set; }
    void SaveInstanceData(int objectIndex)
    {
		_landTransform = new Vector3(objectIndex,0f,0f); 
    }
}

[Serializable]
public struct SpellData
{
    public bool isActiveSkill;
    public float cooldownTime;
}

[Flags]
public enum AttackModes
{
// Decimal
 None = 0,								// 000000
 Melee = 1,								// 000001
 Ranged = 2,							// 000010
 Special = 4,							// 000100
 MeleeAndSpecial = Melee | Special	    // 000101
}


```# UnityCodeStyleGuide
