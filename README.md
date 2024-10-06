# Overview
## Unity C# Coding Style Guide


```CSharp

// Example 1: General Coding Style
public class GameManager : MonoBehaviour
{
    private int _playerScore;
    public int PlayerScore => _playerScore;

    public void AddScore(int points)
    {
        _playerScore += points;
    }
}

// Example 2: Class and Method Declaration
public class GameManager : Singleton<GameManager>
{
    public int MaxHealth { get; private set; }

    public void StartGame()
    {
        InitializePlayer();
    }

    private void InitializePlayer()
    {
        // Logic to initialize the player
    }
}

// Example 3: Properties
public int MaxHealth { get; private set; } // Auto-property

// Example 4: Fields and Variables
[SerializeField] private Transform _playerTransform;
[SerializeField] private bool _isPlayerActive;

void Start()
{
    _isPlayerActive = true;
}

// Example 5: Events
public event Action<int> EventPointsScored;

private void OnPointsScored(int points)
{
    EventPointsScored?.Invoke(points);
}

// Example 6: Enums
[Flags]
public enum AttackModes
{
    None = 0,       // 000000
    Melee = 1,      // 000001
    Ranged = 2,     // 000010
    Special = 4,    // 000100
    MeleeAndSpecial = Melee | Special // 000101
}

// Example 7: Structs
[Serializable]
public struct SpellData
{
    public bool IsActiveSkill;
    public float CooldownTime;
}

// Example 8: Singleton Pattern
public class GameManager : Singleton<GameManager>
{
    // Singleton logic here
}

// Example 9: Serialization
[Serializable]
public class PlayerData
{
    [SerializeField] private int health;
    [SerializeField] private string playerName;
}

// Example 10: Inspector Attributes
[Header("Player Settings")]
[Range(0, 100)]
[SerializeField] private int maxHealth;

// Example 11: Comments and Documentation
/// <summary>
/// Saves the game data for the current session.
/// </summary>
public void SaveGameData()
{
    // Logic to save game data
}

// Example 12: Naming Conventions
private const int MAX_PLAYERS = 4;
private int _currentPlayers;

// Example 13: Conditionals and Loops
if (isPlayerActive)
{
    ActivatePlayer();
}

// Example 14: Performance Considerations
private void Update()
{
    if (isPlayerMoving)
    {
        MovePlayer();
    }
}

// Example 15: Folder Structure Example
/*
Assets/
  ├── Scripts/
  ├── Prefabs/
  ├── Materials/
  ├── Scenes/
*/

// Example 16: Comprehensive Code Usage
using System;
using UnityEngine;

public class GameManager : Singleton<GameManager>
{
    [SerializeField] private Transform _playerTransform;
    [SerializeField] private int _maxHealth;

    public event Action<int> EventHealthChanged;

    public int MaxHealth => _maxHealth;

    void Start()
    {
        InitializePlayer();
    }

    private void InitializePlayer()
    {
        if (_playerTransform != null)
        {
            // Logic to position the player
            _playerTransform.position = Vector3.zero;
        }
        else
        {
            Debug.LogError("[GameManager][InitializePlayer] Player Transform is null.");
        }
    }

    public void AdjustHealth(int value)
    {
        _maxHealth += value;
        EventHealthChanged?.Invoke(_maxHealth);
    }

    private void Update()
    {
        // Example of a conditional Update method
        if (Input.GetKeyDown(KeyCode.Space))
        {
            AdjustHealth(-10);
        }
    }
}
```

